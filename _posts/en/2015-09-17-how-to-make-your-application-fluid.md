---
layout: post
title:  "How to Make Your Application Fluid"
author: junfeng/sarvar
name: "fluid app"
lang: "English"
comments: true
visible: true
mainpic:
youMayAlsoLike: "fluid app"
tags:
    - Development
    - Technology
    - Android
    - Optimization
    - Software

imageUrl: assets/process.png
categories: en post
category: Design
---

In [a previous blog post]({{ site.url }}{{ site.baseurl }}/2015/09/03/why-you-should-care-about-app-performance.html), we discussed the importance of monitoring your app's performance. This time, we’ll show you exactly how to go about doing this.  We’ve spoken with several developer teams from some of the most popular apps in the world, including WeChat and Yahoo News Digest, about the best practices towards building fluid apps. From our own experiences and our talks with these leading developers, we’ve found that the most important practice in building great apps is  **establishing a performance optimization process**:

<figure><img
src="/assets/process.png" alt="Process: measure, analyze, optimize"><figcaption style="text-align: center">
The optimization process </figcaption></figure>


It’s important to continuously measure your app’s performance to detect when your app underperforms.  Once a performance issue is detected, you should focus your energy on finding the root of the issue. This diagnosis may require even more measurements and detailed performance data, trapping you in what we like to call the “measure-analyze loop” for a while.  Even after you track down the root cause of the issue, just fixing the sluggish code is not enough. You have to re-evaluate your app’s metrics to ensure your fix has worked. This means more measurements.

### **Measure**

There are two performance metrics that most affect user experience (UX).  First, we'll focus on response time: how long it takes your app to respond to a user action (like  starting your app, viewing a news article, loading a contact list, or checking a Facebook page). Ideally, your application responds quickly in all of these scenarios, helping you build a better, more engaging UX.

One crucial (and unique) case of response time is start time. App startup is the first experience a user has with an app, and first impressions have never been more important.  In fact, one Compuware study found that [79% of users would retry a problematic app only once or twice before deleting it](https://info.dynatrace.com/rs/compuware/images/Mobile_App_Survey_Report.pdf).

Here are some recommendations from we here at NimbleDroid, who have had years of experience with software performance and optimization.

We suggest that your application take no more than 2 seconds at startup, as this is [the median start time users expect](https://info.dynatrace.com/rs/compuware/images/Mobile_App_Survey_Report.pdf).  For those familiar with web performance, [47% of users expect a page to load within 2 seconds or less](https://blog.kissmetrics.com/loading-time/), and users have [even less patience for mobile apps](http://investor.compuware.com/releasedetail.cfm?releaseid=592528), which they tend to use in a hurry and on-the-go.


<div class="recommendation">
  <div class="recommendation-bar"></div>
  <div class="recommendation-content">
    <h4>Recommendation 1: limit app startup to 2 seconds</h4>
  </div>
</div>


The second important metric is smoothness. While it is great to have a short overall response time, responses themselves must also be smooth, with minimal “lag.”  Users are very good at detecting temporal lags, which means even small stutters can reflect poorly on your app’s UX.  [On average, humans can detect lag as short as 22ms, and a fourth of the population can perceive lag between 2ms and 16ms](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC2826883/figure/F2/) --  thus the standard 60 frames per second (FPS) refresh rate.

To understand smoothness, you can collect your app’s [FPS and frame timing data](https://developer.android.com/preview/testing/performance.html). However, keep in mind that this data doesn’t tell you the source of your app’s performance issues, which means it can't help identify the methods that cause your app to lag.

In Android, the UI thread (your app’s main thread of execution) is the only thread that can update the UI. To maintain a 60 FPS refresh rate, the UI thread must finish drawing each frame in ~16ms.  If any method call in the UI thread runs for longer than this time, your app has to miss a frame, generating a temporal lag.  What's even worse is that during this period, your app is not responsive to any user actions because the UI thread is stuck within a method call.

In practice, it’s nearly impossible to ensure that each and every method call in the UI thread lasts shorter than 16ms. A threshold of 32ms, equivalent to two dropped frames, is more realistic. We call methods that exceed this threshold (those that take over 32ms to execute) [*hung methods*](https://nimbledroid.com/help) because they cause an app to appear to “hang.” Eliminating all hung methods goes a long way towards making your app appear smoother, providing a better overall user experience.


<div class="recommendation">
  <div class="recommendation-bar"></div>
  <div class="recommendation-content">
    <h4>Recommendation 2: eliminate hung methods</h4>
  </div>
</div>




Okay, great. It’s important to measure metrics relevant to the UX, but how often should we be measuring these metrics? Per build? Per daily build? Before each release? In production?!  You should measure whenever you get the chance - the more often you track your software's metrics, the earlier you can detect and respond to performance issues. The Yahoo team we spoke with profiles their app’s performance before each release, and the WeChat team profiles their app per daily build.

<div class="recommendation">
  <div class="recommendation-bar"></div>
  <div class="recommendation-content">
    <h4>Recommendation 3: measure as often as you can</h4>
  </div>
</div>


### **Analyze**


The key to optimizing your software is to be aware of a common set of performance issues and systematically remove them from your code.  In our analysis of performance issues in apps with over 5M downloads, we saw that developers often use constructs that are fast on desktops but significantly slower on wimpier mobile hardware. For instance, method <code>ClassLoader.getResourceAsStream()</code> takes ~7ms on a MacBook Air for a JAR with 3K resources, while it takes ~1700ms on a Nexus 7 2013 for an APK with 3K resources.  It turns out that Android’s implementation of <code>getResourceAsStream</code> does a whole lot of extra work the first time it’s called, indexing all resources in the APK file, verifying the certificate of the APK file, and parsing its manifest.  Operations like these are very CPU intensive, causing extensive app slowdown - <code>getResourceAsStream</code> slows down the Walgreens app by 1.7 seconds. At NimbleDroid, we’ve compiled a list of methods to avoid in your android app. You can check it out [here](https://nimbledroid.com).


<div class="recommendation">
  <div class="recommendation-bar"></div>
  <div class="recommendation-content">
    <h4>Recommendation 4: know a set of common issues</h4>
  </div>
</div>

Sometimes performance issues stem from the 3rd-party SDKs you use, not your code.  These issues can be especially hard to track down. Consider <code>org.joda.time</code>, a popular time library for Java. You’ve probably used it in your prior Java projects.  It turns out that creating just one <code>org.joda.time.DateTime()</code> object during your app’s startup causes a significant slowdown -   the [Yahoo Fantasy Sports app saw a performance drop of 2 seconds](https://nimbledroid.com/play/com.yahoo.mobile.client.android.fantasyfootball?p=2DH2RIaB5laac7#model.FantasyTimeFormatConstants%20static%20initializer). This is because <code>org.joda.time.DateTime()</code> uses <code>getResourceAsStream()</code> to load timezone data from the APK file.


<div class="recommendation">
  <div class="recommendation-bar"></div>
  <div class="recommendation-content">
    <h4>Recommendation 5: avoid surprises in 3rd-party SDKs</h4>
  </div>
</div>

### **Optimize**
Fixing sluggish code can be a nightmarish process. There are hundreds of processes that can cause apps to grind to a halt, and rooting out the source of this slowdown can be a task that takes weeks of development time. Nonetheless, there are some general fixing guidelines. You can either make code run faster using more efficient data representations, algorithms, and implementations or (in the case that you can’t directly fix the code because you’re using an SDK) you can invoke the code in a background thread so it doesn’t hang in your UI. Following these guidelines can go a long way towards making your app more efficient, creating a product users will love.
<br>
<br>

### **Where You Can Get Help**
While this performance optimization process helps make your app fluid, it often requires valuable time and a little bit magic to carry out.  This is exactly why we're working to bring Android devs fast, powerful optimization and profiling tools, so that you guys can focus on what you do best: bringing users an amazing product.
<br>
