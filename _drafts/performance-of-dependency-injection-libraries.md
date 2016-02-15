---
layout: post
title:  "Comparing the Performance of Dependency Injection Libraries"
author: antonkrasov
name: "injection"
lang: "English"
comments: true
visible: true
---

The dependency injection has become an increasingly popular tool in Android development, and for good reason. Injections reduce the amount you have to code (and hence, debug), facilitating the creation of better apps and a smoother development process. While it may be tempting to toss in dependencies to a variety of libraries, it's also important to keep in mind the potential toll that dependency injections can have on your application's performance. To help you navigate through the pros and cons of dependencies, we're going to compare three of the most popular libraries from a performance point of view.

<!-- Dependency injection has become an increasingly popular tool in Android development these days. Since there already exist many articles that answer basic questions like: “Why should I use DI?” or “What libraries can I use for this in Android development?” I want to look at something different today. Rather than discussing DI in general or a specific library, lets compare three of the most popular libraries from a performance point of view. -->

We'll compare:

1. [Roboguice](https://github.com/roboguice/roboguice){:target="_blank"}
2. [Dagger1](http://square.github.io/dagger/){:target="_blank"}
3. [Dagger2](http://google.github.io/dagger/){:target="_blank"}

Roboguice and Dagger work in different ways - the first uses reflection and dagger uses Java compile-time annotation processors to generate code at compile time. Of course, this variation has a huge effect on an application's performance. It's often tempting to opt for the easier to use Roboguice, despite its drawbacks in performance. Yet this is precisely the kind of thinking that should be avoided - the extra effort is more than worth the increased performance.

<!-- This variation has a huge effect on performance of course, but can we measure the difference in exact numbers? At first, you might think “Yeah, I know that roboguice slower than dagger, but that shouldn't be a large issue. Plus it’s easier to use”. In this post, I'll try to show why this is the wrong line of thinking, and why you should take performance seriously. -->

<!-- Here I've created a repo with 3 demo apps: [https://github.com/NimbleDroid/DIDemoApps](https://github.com/NimbleDroid/DIDemoApps){:target="_blank"}
(Repository contains some spoilers :) ) -->

We've created a [github repository](https://github.com/NimbleDroid/DIDemoApps){:target="_blank"} with three demo apps. Take a moment to check it out - it should be pretty easy to understand what's going on if you've used any of these libraries before. All these apps have the same graph, and we inject dummy objects to calculate the DI overhead. We also output some logs in order to confirm that the injections are successful.

In total we do 5455 injections: <br>
1. 4800 model classes (A* .. F*) into Test* <br>
2. 600 Test* classes into TestManager* <br>
3. 40 Test* classes into MainActivity <br>
4. 15 TestManager clases into MainActivity <br>

(Library specific features, like views injection in Roboguice, aren't used).

<br>

For time measurements we'll use [nimbledroid.com](https://nimbledroid.com). Here are results on the same dummy app, using the three different libraries we mentioned earlier.

1. [Roboguice](https://nimbledroid.com/play/com.nimbledroid.demo.roboguice?p=2xemuybOQl465K#Summary){:target="_blank"}
2. [Dagger1](https://nimbledroid.com/play/com.nimbledroid.demo.dagger1?p=2xenuDYYAddw8e#Summary){:target="_blank"}
3. [Dagger2](https://nimbledroid.com/play/com.nimbledroid.demo.dagger2?p=2xeo7Q6EznQ9Pz#Summary){:target="_blank"}

All this data can be kind of confusing, so we'll walk you through it.

By default, NimbleDroid will display the general [cold startup time](link to cold start post) of the app. We can check out the performance of specific methods by navigating to Analysis Details -> Icicle Graph. Here, you should see something like this:

<figure><img src="{{ site.baseurl }}/assets/di/roboguice_icicle_graph.png" alt="Roboguice Iricle Graph" /></figure>

Surprisingly, Roboguice takes an entire **3923ms** to inject! That’s a tremendous overhead. The problem is further exacerbated when we take into account the fact that this injection is only used in conjunction with dummy objects - in a real application, injected objects will initialize other objects, and this in turn will require additional time to process. It's important to realize that this injection is simply not worth it. After all, [the recommended cold startup time is ~2 seconds]({{ site.url }}{{ site.baseurl }}/2015/09/17/how-to-make-your-application-fluid.html), but we've already spent ~4 seconds just on dependency injections.

Ok, now let’s compare this with Dagger 1 and Dagger 2 results.

Dagger 1:

<figure><img src="{{ site.baseurl }}/assets/di/dagger_1_iricle_graph.png" alt="Dagger 1 Iricle Graph" /></figure>

Dagger 2:

<figure><img src="{{ site.baseurl }}/assets/di/dagger_2_iricle_graph.png" alt="Dagger 2 Iricle Graph" /></figure>

As you can see , Roboguice is 25 times slower then Dagger 1. Dagger 2 is slightly faster than Dagger 1, taking 64ms to inject as opposed to Dagger 1's 154ms.


### **Real world examples**

Now let’s examine some actual apps. One of the nicest examples for this is Skype.

In older versions, [Skype used Roboguice for injections](https://nimbledroid.com/play/com.skype.raider?p=2KuUa7YYy9GRMP#Icicle%20Graph){:target="_blank"}:

<figure><img src="{{ site.baseurl }}/assets/di/old_skype_iricle_graph.png" alt="Old skype icicle graph"/></figure>

As you can see, it takes 2415ms for injection when they used Roboguice.

Over time, however, they [switched to Dagger](https://nimbledroid.com/play/com.skype.raider?p=2LAo9wuOydjFFW#Icicle%20Graph){:target="_blank"}, reducing injection time to a bare 170ms:

<figure><img src="{{ site.baseurl }}/assets/di/new_skype_iricle_graph.png" alt="New skype iricle graph" /></figure>


#### **Here are some popular apps with similar problems:**

1. [Amex Mobile](https://nimbledroid.com/play/com.americanexpress.android.acctsvcs.us?p=2EGfUBezmegtLv#Icicle%20Graph){:target="_blank"} (~1.7 sec overhead)
2. [Fandango Movies](https://nimbledroid.com/play/com.fandango?p=2DGLCuvSR5Gpzs#Icicle%20Graph){:target="_blank"} (~5 sec overhead)
3. [Soundwave Music Discovery](https://nimbledroid.com/play/me.soundwave.soundwave?p=24MwnhizE3OlxB#Icicle%20Graph){:target="_blank"} (~2.3 sec overhead)

### **One more thing**

There's also one more significant drawback to using Roboguice. Going to the App Info of our dummy Roboguice app, we see this:

<figure><img src="{{ site.baseurl }}/assets/di/roboguice_app_info.png" alt="Roboguice app info" /></figure>

Under the "Method Count" section, NimbleDroid tells us that using Roboguice requires calls to 33,189 methods.

Now let’s look at Dagger 1:

<figure><img src="{{ site.baseurl }}/assets/di/dagger_1_app_info.png" alt="Dagger 1 app info" /></figure>

and Dagger 2:

<figure><img src="{{ site.baseurl }}/assets/di/dagger_2_app_info.png" alt="Dagger 2 app info" /></figure>

33200 methods vs 24000 methods! Android has a 65k method limit for single dex files, so ~10000 methods can make a huge difference. Using Roboguice also adds about 300kb to the final APK size.

Note: we didn't use proguard for these tests, as we wanted to check library overheads without post optimizations.

<div class="recommendation">
  <div class="recommendation-bar"></div>
  <div class="recommendation-content">
    <h4>Recommendation: Avoid Roboguice in your Android apps.  Use Dagger 2 if you can. </h4>
  </div>
</div>

<a href="https://nimbledroid.com/upload_apk"><button class="call-to-action"> See how dependency injection affects your own app </button></a>
