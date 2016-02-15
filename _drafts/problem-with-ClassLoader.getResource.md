---
layout: post
title:  "The Problem with ClassLoader.getResource*"
name: "getResource"
lang: "English"
comments: true
author: junfeng/sarvar
visible: true
---

Through our analysis at NimbleDroid, we've picked up on a few tricks that help prevent monolithic lags in your applications, boosting fluidity and response time. One of the things we've learned to watch out for the dreaded getResourceAsStream, a method that causes gigantic slowdown. Of all of the apps that we've analyzed (and we've analyzed [a ton of apps](https://nimbledroid.com/play)), we've seen that nearly 20% are affected by ClassLoader.getResource. Of these, some of the most notable are mobileCore (whose implementation of the method [significantly](link to first blog) slows down over 250 apps), StartApp, Joda-Time, and RoboGuice.

We looked at 7,500 top apps on the Google Play store, and were surprised to see that over 10% of these apps saw substantial slowdown as a direct result of their implementation of the method. Amazon's Kindle app for Android, which has [over 100 million downloads](https://play.google.com/store/apps/details?id=com.amazon.kindle&hl=en), has over 1315ms of delay (data from 1/12/16) as [a result of the method's usage](https://nimbledroid.com/play/com.amazon.kindle?p=2LBiUc6W69S6El#RoboGuice.getPropertiesFromClassLoader). On the PC, Kindle takes only [[[[GETDATA]]]] time to run. Juxtapose the two numbers and it becomes clear that getResourceAsStream is a serious concern, one that is almost guaranteed to cripple an app's growth.

XXX show stats of 15 top apps affected by getResource
    number of downloads
    size of APK file
    delay added

com.amazon.kindle
tunein.player
com.sgiggle.production
com.mobilemotion.dubsmash
com.sirma.mobile.bible.android
com.melodis.midomiMusicIdentifier.freemium
com.badoo.mobile
com.outfit7.talkingangelafree
com.loudtalks
com.quvideo.xiaoying
com.smule.magicpiano
cn.jingling.motu.photowonder
com.audible.application
com.WaterfallLiveWallpaper
me.everything.launcher
com.fatsecret.android

Despite being one of the highest ranked apps on the Google Play store, the TuneIn radio app has one of the [highest startup times among top apps](https://nimbledroid.com/play/tunein.player?p=2DHCUbrou1eJEx#Summary). This time, the method's impact is even more drastic: [it causes 1447ms of lag](https://nimbledroid.com/play/tunein.player?p=2DHCUbrou1eJEx#ZoneInfoProvider.openResource). The method takes up more CPU time than every other problem method, combined.

We've compiled a [list of SDKS affected](link list here) so you know what to watch out for when developing your own applications down the line.


XXX show stats of 15 SDKs that affected the most number of apps
   number of apps affected
   average delay added
mobileCore
SLF4J
StartApp
Joda-Time
TapJoy
Google Dependency Injection
BugSense
RoboGuice
OrmLite
Appnext
Apache log4j
Twitter4J
Appcelerator Titanium
LibPhoneNumbers (Google)
Amazon AWS


getResource methods add an average startup delay of _____ seconds, which could be the difference in whether a user decides to continue using an app, or whether consumers leave positive or negative reviews.


<div style="margin: 0 auto;">
  <canvas id="sdks" height="500" width="600"></canvas>
</div>

###What is ClassLoader?
The ClassLoader class instantiates objects responsible for finding and loading classes to be used among other code. However, Android applications use subclasses of CLassLoader to specify the way in which JVM dynamically loads classes. ClassLoader instances are also responsible for linking and initializing Java classes and creating the JVM infrastructure needed to implement internal data structures within Classes. It also plays a role in Java's automatic memory allocation process (termed garbage collection). As a result, classes are unloaded when their respective ClassLoaders have no reference. Clearly, ClassLoader is an integral part of an Android Application - so what's so wrong about it's use?


###Why is ClassLoader so slow?
Well, it's all about how and where <code>ClassLoader</code> objects are being used. Part of the issue is that Java was initially intended for desktop computers, which have significantly more powerful processing capabilities than mobile devices. As such, code that takes negligible time on a desktop could cause significant delays in the startup time (or overall performance) of a mobile application.

What's really happening is that  methods of the <code>ClassLoader</code> class like <code>.getResourceAsStream</code> require that files be unzipped out of the APK, even if the data you are trying to access is cached. Unfortunately, many SDKs still seem to implement such methods, despite the existence of [faster alternatives](https://github.com/googlei18n/libphonenumber/issues/940) (SHOULD WE INCLUDE THAT LINK?) like <code>AssetManager.open()</code> or <code>Resources.openRawResource</code>.

The prevalence of <code>ClassLoader</code> methods like <code>getResourceAsStream</code> only serves to highlight how important it is to be _continuously profiling your code_. Avoiding ill-suited methods like these go a long way towards cutting start time and providing a cleaner user experience and creating a better app. As a final note, we've graphed the average increase in initialization time of apps as a result of their SDKs calling <code>ClassLoader.getResource()</code>. These SDKs have frighteningly large load times - apps built with popular SDK Joda-Time have an average increase in startup time that exceeds 650ms!

<div style="margin: 0 auto;">
  <canvas id="init-times" height="500" width="600"></canvas>
</div>


<a href="https://nimbledroid.com/upload_apk"><button class="call-to-action" style="font-size:12; padding:10px; padding-bottom:49px; padding-top: 13px;"> Eliminate <code>ClassLoader.getResource()</code> from your application </button></a>

#priorities/needs expansion
- Average startup delay it adds


- Apps affected: list popular ones

<script>

window.onload = function(){
  var sdks = document.getElementById("sdks").getContext("2d");

  window.myBar = new Chart(sdks).Bar(sdkData, {
    responsive : true
  });

  var init_times = document.getElementById("init-times").getContext("2d");

  window.myBar = new Chart(init_times).Bar(initTimes, {
    responsive : true
  });
}

var sdkData = {
    labels: ['mobileCore', 'SLF4J', 'StartApp', 'Joda-Time', 'TapJoy', 'Google Dependency Injection', 'BugSense', 'RoboGuice', 'OrmLite', 'Appnext', 'Apache log4j', 'Twitter4J', 'Appcelerator Titanium', 'LibPhoneNumbers (Google)', 'Amazon AWS', 'Spring Framework', 'Chartboost', 'Smack', 'Pollfish', 'Jsoup', 'Baidu', 'Open Street Map Tools', 'PrettyTime', 'Paypal', 'Mobclix', 'Smaato', 'Fyber', 'libGDX', 'Nuance', 'Apache Thrift', 'Cocos2d Game Framework', 'Jackson', 'Google Data Lib', 'MobFox', 'Guava Core Libs', 'Thoughtworks XStream', 'Amazon Mobile Ads', 'Signal360', 'ORMMA', 'JBoss', 'Charting Library for Android', 'Socialize', 'XML Pull'],
    datasets: [
        {
            label: "Cold Start Times",
            fillColor: "#ff0000",
            strokeColor: "#ff0000",
            highlightFill: "#cc0000",
            highlightStroke: "#cc0000",
            data: [251, 70, 67, 55, 52, 46, 41, 35, 26, 25, 25, 24, 21, 18, 18, 18, 16, 13, 8, 8, 5, 5, 4, 4, 4, 3, 3, 3, 2, 2, 2, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
        },
    ]
};

var initTimes = {
    labels: ['TapJoy', 'Joda-Time', 'Smack', 'Nuance', 'Amazon AWS', 'Appcelerator Titanium', 'AppMK Book/Magazine Maker', 'Jsoup', 'SLF4J', 'StartApp', 'Getjar', 'Google Dependency Injection', 'svg-android', 'Simple XML Framework', 'Appnext', 'Google Data Lib', 'libGDX', 'ORMMA', 'Janrain Engage', 'mobileCore', 'Metaps', 'Android Query', 'Google-My Json', 'Open Street Map Tools', 'Jerico HTML Parser', 'Gson', 'Livestream', 'Spring Framework', 'Adobe Air', 'OAuth', 'RoboGuice', 'GNU Kawa', 'OrmLite', 'Apache log4j', 'Socialize', 'Guava Core Libs', 'Twitter4J', 'Google Play License', 'RevMob', 'RobotMedia Billing', 'Apache Thrift', 'Corona Mobile SDK', 'Google Play Licensing', 'Android Asynchronous Http Client', 'Baidu', 'Paypal', 'InMobi', 'Google Ads', 'MobileAppTracking'],
    datasets: [
        {
            label: "Cold Start Times",
            fillColor: "#ff0000",
            strokeColor: "#ff0000",
            highlightFill: "#cc0000",
            highlightStroke: "#cc0000",
            data: [663.1205264, 657.1752479, 626.6743532, 612.4041995, 592.4237224, 558.105627, 532.329, 512.5169933, 440.2982676, 436.7717586, 382.435104, 379.3869451, 342.92502, 327.8869057, 299.7976912, 296.939928, 292.2991978, 279.186902, 272.6641225, 267.1751023, 242.9524783, 223.07173, 220.545232, 208.7320996, 196.972688, 186.3575278, 178.412687, 168.4566834, 168.278046, 165.420659, 158.9790431, 145.159554, 133.7474456, 121.7079672, 121.572953, 119.9312396, 119.015194, 117.056682, 116.8943707, 113.277929, 109.5168813, 105.6278439, 101.2758637, 100.2629045, 88.95902504, 87.90472067, 83.2441999, 81.0690283, 80.77897946]
        },
    ]
};
