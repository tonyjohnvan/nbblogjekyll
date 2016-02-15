---
layout: post
title:  "Working with Data in the Main Thread"
author: antonkrasov
name: "main thread"
lang: "en"
comments: true
visible: true
---

Nearly all Android apps require working with some form of data, and over the past few years, JSON has become one of the most widely used infrastructures for storing and accessing data. A plethora of new libraries have sprung up as a result of JSON's new popularity: GSON, Jackson, etc.

Every experienced Android developer knows that executing network requests and parsing data should be avoided on the main thread whenever possible. But since there are some who still work with data in the main thread, let's check out how much this can affect performance.

Let's check out an example. Here's an old version of the app we'll be looking at: [Hollister v3.1.2](https://nimbledroid.com/play/com.abercrombie.hollister?p=24MpWQo0PFe7cX#Icicle%20Graph){:target="_blank"}  

<figure><img src="{{ site.baseurl }}/assets/working-with-data-in-main-thread/prefetchData.png" alt="Hollister v3.1.2 Icicle Graph" /></figure>

As you might have already noticed, method [AFSDK.prefetchData()](https://nimbledroid.com/play/com.abercrombie.hollister?p=24MpWQo0PFe7cX#AFSDK.prefetchData()){:target="_blank"} takes 5709ms to run!

We see that the main cause of the delay is ObjectMappger.readValue() (from the [Jackson](http://wiki.fasterxml.com/JacksonHome){:target="_blank"} library). As a result, users need to wait an entire **5** additional seconds for the app to finish parsing data.

Fortunately, developers eventually caught their mistake and were able to fix the issue in a newer version, drastically increasing their application's performance (and, as a result, their users' happiness).

<figure><img src="{{ site.baseurl }}/assets/working-with-data-in-main-thread/new_version.png" alt="Hollister v4.0 Icicle Graph" /></figure>

2.2 seconds for the new cold-start time, a **huge** improvement from 5.2 seconds.  

Let’s take a closer look at the icicle graph:

<figure><img src="{{ site.baseurl }}/assets/working-with-data-in-main-thread/new_version_icicle_graph.png" alt="Hollister v4.0 Icicle Graph" /></figure>

As you can see, this wasn't a super complicated fix - developers simply moved the parsing of a large initial config into another thread (using the popular [RxJava](https://github.com/ReactiveX/RxJava){:target="_blank"} library).

#### **Popular Apps with the Same Issue**

1. [eBay (~500ms)](https://nimbledroid.com/play/com.ebay.mobile?p=2DGJh7FgPtnG20#Icicle%20Graph){:target="_blank"}
2. [Fox News (~500ms)](https://nimbledroid.com/play/com.foxnews.android?p=2LAX4s1ZyB8ZS5#Icicle%20Graph){:target="_blank"}
3. [IMDb (~300ms)](https://nimbledroid.com/play/com.imdb.mobile?p=2LAn6wgZpKR1wK#Icicle%20Graph){:target="_blank"}
3. [BBC News (~2600ms)](https://nimbledroid.com/play/bbc.mobile.news.ww?p=2LBxzUaCTqL6AD#Icicle%20Graph){:target="_blank"}

#### **Parsing a Response in the Main Thread**

[Akinator FREE app](https://nimbledroid.com/play/com.digidust.elokence.akinator.freemium?p=2LBUuOaCBZDgpV#Icicle%20Graph){:target="_blank"}

<figure><img src="{{ site.baseurl }}/assets/working-with-data-in-main-thread/scanner.png" alt="Akinator FREE app Icicle Graph" /></figure>

Here's another common issue. When we execute a network request, we'll sometimes receive a string as the result. Some apps will proceed to parse the resulting string in the main thread, using XML, JSON or some other method of parsing data. The example app above parses data with the java.util.Scanner class, which, as you can see, is not very fast: 192 calls take up 279 ms.    

#### **Other Interesting Cases**

Let’s examine a few other interesting cases that can potentially cause huge delays.

#### **[bitcoinj library:](https://bitcoinj.github.io/){:target="_blank"}**

Here's [Wiper](https://nimbledroid.com/play/com.gowiper.android?p=2LBWGdxbz40SmJ#Icicle%20Graph){:target="_blank"}, a free messaging and calling app that incorporates music and video sharing.

<figure><img src="{{ site.baseurl }}/assets/working-with-data-in-main-thread/bitcoinj.png" alt="Wiper app Icicle Graph" /></figure>

It takes over 4 seconds to initialize a single library!

#### **[Charset.availableCharsets())](http://developer.android.com/reference/java/nio/charset/Charset.html#availableCharsets()){:target="_blank"}**

Here's another popular app: [FIFA](https://nimbledroid.com/play/com.fifa.fifaapp.android?p=2LSQeDAWrp2F6y#converter.StringHttpMessageConverter%20constructor){:target="_blank"}

<figure><img src="{{ site.baseurl }}/assets/working-with-data-in-main-thread/availableCharsets.png" alt="FIFA app Icicle Graph" /></figure>

For some reason this method call takes 270ms. The problem is somewhere deep in the SDK, but please note that this issue might be device specific.

#### **[java-aes-crypto library](https://github.com/tozny/java-aes-crypto){:target="_blank"}**

We see another big issue with: [Kaave Falı](https://nimbledroid.com/play/com.didilabs.kaavefali?p=2LRJ9SvzEgS0qH#AesCbcWithIntegrity.generateKeyFromPassword){:target="_blank"}

<figure><img src="{{ site.baseurl }}/assets/working-with-data-in-main-thread/aes-crypto.png" alt="Kaave Falı app" /></figure>

Generating cryptographic keys in the main thread isn't a great idea, especially on low end mobile devices.

#### **[AssetManager.list()](http://developer.android.com/reference/android/content/res/AssetManager.html#list(java.lang.String)){:target="_blank"}**

And one last app: [Talking James Squirrel](https://nimbledroid.com/play/com.kauf.talking.baum.TalkingJamesSquirrel?p=2L9rN3y7GP1kMc#FrameAnimation.loadResource){:target="_blank"}

<figure><img src="{{ site.baseurl }}/assets/working-with-data-in-main-thread/AssetManager.getList().png" alt="Kaave Falı app" /></figure>

Remember that the more assets you have, the more time this method call will take.
