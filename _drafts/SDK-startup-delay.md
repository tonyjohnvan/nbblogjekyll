---
layout: post
title:  "Performance problems in libraries and SDKs"
name: "SDK problems"
author: antonkrasov
comments: true
visible: true
lang: English
---

It's hard to imagine modern android apps without some libraries and SDKs inside. Most of apps have some network and image loading libraries and/or crashes tracking, advertisement or analytics SDKs inside. During checking lots of performance problems, we found that some libraries SDKs are main cause of huge delays.

### ****

### **Most common problems for libraries and SDKs:**

#### **[ClassLoader.getResource](#) <a name="ClassLoader.getResource">&nbsp;</a>**

This is the most popular performance issue ([READ MORE](#) **TODO: ADD LINK**). This issue is very popular in libraries and SDKs, because if you provide lib as JAR file, that's the only way, how you can load resources. There are lots of reasons, why developers can prefer JAR to AAR ([more info about AAR format](http://tools.android.com/tech-docs/new-build-system/aar-format){:target="_blank"}). They are:

1. One distribution package for both Java world and Android
2. Historical reasons (library is very old, or SDKs started developing before AAR was introduced)
3. Developers know how to build JAR libraries and don't want to learn how to work with AAR

#### **[Working with data in main thread](#) <a name="working-with-data-in-main-thread">&nbsp;</a>**

This issue is also easy to understand, SDK developers require some initialization, for example Advertisement SDKs need to know list of installed apps (to avoid showing you Ad for apps you already have). Some A/B testings SDKs need to load config. Some SDKs implemented initialization with long running tasks in MAIN thread with slow down your app a lot.

[READ MORE](#) **TODO: ADD LINK**

#### **[Reflection](#) <a name="reflection">&nbsp;</a>**

This issue is more spread in libraries. The idea is that library developers want to make life of others much more easier, Java language give them huge abilities with help of Annotations and Reflection. So you can configure REST client with help of annotations, or just describe your models with them and library will do all other work, like creating DAO objects for your models. Looks like a great thing, but this method adds lots of performance problems to your apps [READ MORE](#) **TODO: ADD LINK**

### **Real libraries and SDKs problems with examples in real apps**

<!-- 
<a href="#ClassLoader.getResource">ClassLoader.getResource</a> <br>
<a href="#working-with-data-in-main-thread">Working with data in main thread</a> <br>
<a href="#reflection">Reflection</a> <br>
 -->          

Navigation: 

 1.  <a href="#Tapjoy">Tapjoy</a>
 2.  <a href="#Startapp">Startapp</a>
 3.  <a href="#Heyzap">Heyzap</a>
 4.  <a href="#Yume">Yume</a>
 5.  <a href="#Joda-Time">Joda-Time</a>
 6.  <a href="#OrmLite">OrmLite</a>
 7.  <a href="#Activeandroid">Activeandroid</a>
 8.  <a href="#Jersey">Jersey</a>
 9.  <a href="#AWS-Android-SDK">AWS Android SDK</a>
 10. <a href="#SLF4J">SLF4J</a>
 11. <a href="#Logback">Logback</a>

#### **[Tapjoy](https://home.tapjoy.com/){:target="_blank"} <a name="Tapjoy">&nbsp;</a>**

Issue: <a href="#ClassLoader.getResource">ClassLoader.getResource</a>

Example: 

<figure><img src="{{ site.baseurl }}/assets/sdks/tapjoy.png" alt="tapjoy" /></figure>

Some Affected apps: 

1. [textPlus](https://nimbledroid.com/play/com.gogii.textplus?p=2DGMyC8vIXa2qh#Icicle%20Graph){:target="_blank"}
2. [Bible](https://nimbledroid.com/play/com.sirma.mobile.bible.android?p=2DGoBb49fTWxds#Icicle%20Graph){:target="_blank"}
3. [Akinator FREE](https://nimbledroid.com/play/com.digidust.elokence.akinator.freemium?p=2LBUuOaCBZDgpV#Icicle%20Graph){:target="_blank"}
4. [AlarmMon](https://nimbledroid.com/play/com.malangstudio.alarmmon?p=2LAqpm0PD8TX4x#Icicle%20Graph){:target="_blank"}
5. [Yokee](https://nimbledroid.com/play/com.famousbluemedia.yokee?p=2LBqiESOTDBpeo#Icicle%20Graph){:target="_blank"}
6. [Keek](https://nimbledroid.com/play/com.keek?p=2L9LbaHXBzulDt#Icicle%20Graph){:target="_blank"}
7. [SimSimi](https://nimbledroid.com/play/com.ismaker.android.simsimi?p=2DGRIRVLsdilC7#Icicle%20Graph){:target="_blank"}
8. [InstaFisheye](https://nimbledroid.com/play/com.onemanwithcamera.instafish?p=2DGeHZz1RqCN0S#Icicle%20Graph){:target="_blank"}
9. [Jaumo](https://nimbledroid.com/play/com.jaumo?p=2Ma1AUxPhwGGsb#Icicle%20Graph){:target="_blank"}
10. [My Diet Coach](https://nimbledroid.com/play/com.dietcoacher.sos?p=2DGIdLTWxjac4a#Icicle%20Graph){:target="_blank"}
11. [Talking Angela](https://nimbledroid.com/play/com.outfit7.talkingangelafree?p=2DGei9TBXrL0rQ#Icicle%20Graph){:target="_blank"}
12. [ZombieBooth](https://nimbledroid.com/play/com.motionportrait.ZombieBooth?p=2DGc92SLyqPcth#Icicle%20Graph){:target="_blank"}

#### **[Startapp](http://www.startapp.com/){:target="_blank"} <a name="Startapp">&nbsp;</a>**

Issues: 

1. <a href="#working-with-data-in-main-thread">Working with data in main thread</a>
2. <a href="#ClassLoader.getResource">ClassLoader.getResource</a> 

Example: 

<figure><img src="{{ site.baseurl }}/assets/sdks/Startapp.png" alt="Startapp" /></figure>

Some Affected apps: 

1. [Lovely Photo Frames](https://nimbledroid.com/play/com.tndev.loveframes?p=2DGw3u0vMD99QC#Icicle%20Graph){:target="_blank"}
2. [Flash Alerts](https://nimbledroid.com/play/com.fantasticdroid.flashalerts?p=2DGLDh68ScVc9D#Icicle%20Graph){:target="_blank"}
3. [Voice Changer](https://nimbledroid.com/play/com.bruce.android.noid?p=2DGG0VKivuOx40#Icicle%20Graph){:target="_blank"}

#### **[Heyzap](https://www.heyzap.com){:target="_blank"} <a name="Heyzap">&nbsp;</a>**

Issue: <a href="#working-with-data-in-main-thread">Working with data in main thread</a>

3 calls of packageManager.getInstalledPackages(), this takes ~**236ms**

Example: 

<figure><img src="{{ site.baseurl }}/assets/sdks/Heyzap.png" alt="Heyzap" /></figure>

Some Affected apps: 

1. [Mackolik Canlı Sonuçlar](https://nimbledroid.com/play/com.kokteyl.mackolik?p=2DGUfGU6NOjRu7#Icicle%20Graph){:target="_blank"}

#### **[Yume](http://www.yume.com/){:target="_blank"} <a name="Yume">&nbsp;</a>**

Issue: <a href="#ClassLoader.getResource">ClassLoader.getResource</a> 

Example: 

<figure><img src="{{ site.baseurl }}/assets/sdks/Yume.png" alt="Yume" /></figure>

Some Affected apps: 

1. [Talking James Squirrel](https://nimbledroid.com/play/com.kauf.talking.baum.TalkingJamesSquirrel?p=2L9rN3y7GP1kMc#Icicle%20Graph){:target="_blank"}
2. [Talking Babsy Baby: Baby Games](https://nimbledroid.com/play/com.kauf.talking.baum.TalkingBabsyBaby?p=2L9hfZQZEGmaSK#Icicle%20Graph){:target="_blank"}

#### **[Joda-Time](http://www.joda.org/joda-time/){:target="_blank"} <a name="Joda-Time">&nbsp;</a>**

Issue: <a href="#ClassLoader.getResource">ClassLoader.getResource</a> 

Example: 

<figure><img src="{{ site.baseurl }}/assets/sdks/Joda-Time.png" alt="Joda-Time" /></figure>

Some Affected apps: 

1. [Yahoo Fantasy Sports](https://nimbledroid.com/play/com.yahoo.mobile.client.android.fantasyfootball?p=2DH2RIaB5laac7#Icicle%20Graph){:target="_blank"}
2. [TuneIn Radio - Radio & Music](https://nimbledroid.com/play/tunein.player?p=2DHCUbrou1eJEx#Icicle%20Graph){:target="_blank"}
3. [My Pregnancy Today Tracker](https://nimbledroid.com/play/com.babycenter.pregnancytracker?p=2LBnxsElZyNUT9#Icicle%20Graph){:target="_blank"}
4. [LiveScore](https://nimbledroid.com/play/com.livescore?p=2DGVxmu3MDptDJ#Icicle%20Graph){:target="_blank"}
5. [Vevo - Watch HD Music Videos](https://nimbledroid.com/play/com.vevo?p=2DGyyFLprtETqF#Icicle%20Graph){:target="_blank"}
6. [Muslim Pro: Prayer Times Quran](https://nimbledroid.com/play/com.bitsmedia.android.muslimpro?p=2DGFb9Ipti2hoi#Icicle%20Graph){:target="_blank"}
7. [Timehop](https://nimbledroid.com/play/com.timehop?p=2DGvNGHPt4RT7M#Icicle%20Graph){:target="_blank"}

#### **[OrmLite](http://ormlite.com/){:target="_blank"} <a name="OrmLite">&nbsp;</a>**

Issue: <a href="#ClassLoader.getResource">ClassLoader.getResource</a> 

Example:

<figure><img src="{{ site.baseurl }}/assets/sdks/ormlite.png" alt="ormlite" /></figure>

Some Affected apps:

1. [Booking.com Hotel Reservations](https://nimbledroid.com/play/com.booking?p=2LAevyLAo1Ej3X#Icicle%20Graph){:target="_blank"}
2. [Nike+ Running](https://nimbledroid.com/play/com.nike.plusgps?p=2L8gQfE5v08CUl#Icicle%20Graph){:target="_blank"}
3. [Anghami - Free Unlimited Music](https://nimbledroid.com/play/com.anghami?p=2LBsjI2ZPUecOx#Summary){:target="_blank"}
4. [Run with Map My Run](https://nimbledroid.com/play/com.mapmyrun.android2?p=2L9oXPW7IW8m4C#Icicle%20Graph){:target="_blank"}
5. [OLX Brasil - Comprar e Vender](https://nimbledroid.com/play/com.schibsted.bomnegocio.androidApp?p=2DGm4LHVlSa3AC#Icicle%20Graph){:target="_blank"}
6. [Kaave](https://nimbledroid.com/play/com.didilabs.kaavefali?p=2LRJ9SvzEgS0qH#Icicle%20Graph){:target="_blank"}

#### **[Activeandroid](http://www.activeandroid.com/){:target="_blank"} <a name="Activeandroid">&nbsp;</a>**

Issue: <a href="#reflection">Reflection</a>

Example:

<figure><img src="{{ site.baseurl }}/assets/sdks/activeandroid.png" alt="activeandroid" /></figure>

Some Affected apps:

1. [Myntra - Online Shopping App](https://nimbledroid.com/play/com.myntra.android?p=2MaFbQjkB3NqbR#Icicle%20Graph){:target="_blank"}
2. [Scribd - A World of Books](https://nimbledroid.com/play/com.scribd.app.reader0?p=2DGmfF1rC8PO85#Icicle%20Graph){:target="_blank"}

#### **[Jersey](https://jersey.java.net){:target="_blank"} <a name="Jersey">&nbsp;</a>**

Issue: <a href="#reflection">Reflection</a>

Example:

<figure><img src="{{ site.baseurl }}/assets/slow-android-reflection/com.photobucket.android-iricle-graph-bottom.png" alt="com.photobucket.android Iricle Graph" /></figure>

Some Affected apps:

1. [Photobucket - Save Print Share](https://nimbledroid.com/play/com.photobucket.android?p=2DGhhgjWGOFDjP#Icicle%20Graph){:target="_blank"}

#### **[AWS Android SDK](https://aws.amazon.com/mobile/sdk/){:target="_blank"} <a name="AWS-Android-SDK">&nbsp;</a>**

Issue: <a href="#ClassLoader.getResource">ClassLoader.getResource</a> 

Example: 

<figure><img src="{{ site.baseurl }}/assets/sdks/aws.png" alt="AWS" /></figure>

Some Affected apps: 

1. [Moovit: Next Bus & Train Info](https://nimbledroid.com/play/com.tranzmate?p=2DGwZ5zKNRvuiz#Icicle%20Graph){:target="_blank"}

#### **[SLF4J](http://www.slf4j.org/){:target="_blank"} <a name="SLF4J">&nbsp;</a>**

Issue: <a href="#ClassLoader.getResource">ClassLoader.getResource</a> 

Example:

<figure><img src="{{ site.baseurl }}/assets/sdks/slf4j.png" alt="slf4j" /></figure>

Some Affected apps:

1. [Amazon Kindle](https://nimbledroid.com/play/com.amazon.kindle?p=2LBiUc6W69S6El#Icicle%20Graph){:target="_blank"}

#### **[Logback](http://logback.qos.ch/){:target="_blank"} <a name="Logback">&nbsp;</a>**

Issue: <a href="#ClassLoader.getResource">ClassLoader.getResource</a> 

Example:

<figure><img src="{{ site.baseurl }}/assets/sdks/logback.png" alt="logback" /></figure>

Some Affected apps:

1. [Audiobooks from Audible](https://nimbledroid.com/play/com.audible.application?p=2DGEBvcEuZEQyT#Icicle%20Graph){:target="_blank"}
2. [Wiper](https://nimbledroid.com/play/com.gowiper.android?p=2LBWGdxbz40SmJ#Icicle%20Graph){:target="_blank"}
3. [Marco Polo: PTT Video Chat](https://nimbledroid.com/play/co.happybits.anyvideo.kik?p=2L8vo56hU6F8Fy#Icicle%20Graph){:target="_blank"}
4. [Talkatone: FREE Texts & Calls](https://nimbledroid.com/play/com.talkatone.android?p=2DGtmqxauAdlG0#Icicle%20Graph){:target="_blank"}
