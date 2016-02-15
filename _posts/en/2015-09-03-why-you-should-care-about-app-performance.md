---
layout: post
title:  "Why You Should Care about Your Android App's Performance"
author: junfeng/sarvar
name: "why"
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

imageUrl: assets/abc-news-app-negative-review.png
categories: en post
category: Optimization
---

Android is dominating the global and national mobile app market. As a
result, developers are pumping out new apps every day. As early as 2011,
[over 500 new Android apps were being released
daily](http://www.nytimes.com/2011/12/12/technology/one-million-apps-and-counting.html). By
April 2015, the number of Android apps had reached [over 1.4
million](http://www.appbrain.com/stats/number-of-android-apps), and apps
on the Google Play store surpassed a staggering [125 billion
downloads](https://blog.gallop.io/the-2015-edition-app-store-vs-google-play-store/). Not
surprisingly, the market has only continued to grow since.

However, many of these apps have significant delay times that ruin a
potentially amazing user experience. In [one study commissioned by
CompuWare](https://info.dynatrace.com/rs/compuware/images/Mobile_App_Survey_Report.pdf),
of the 56% of respondents who had experienced a mobile app problem in the
past 6 months, a staggering 47% reported that apps were too slow to
launch, while over 60% stated that their apps had crashed, frozen, or
displayed errors they should not have.  While this study considers mobile
apps in general, performance problems tend to occur more in Android than
iOS because of the low-end Android devices in the market and the use of
Java as the main app programming language.

Unfortunately, users have no patience for sluggish apps: [AppDynamics
reports that 86% of users have uninstalled apps after only using them once
due to their sluggish
performance](http://www.appdynamics.com/media/uploaded-files/1425406960/app-attention-span-research-report-1.pdf), and a test by JWPlayer suggests that [70% of your audience will leave within 11 seconds of waiting for content (in this case, a video within an app) to load](http://www.jwplayer.com/blog/improving-hls-android-sdk-1-2/). It is clear (and obvious) that slow apps make users unhappy. Here’s an example of a user’s review of the ABC News app:

<figure><a
href="https://play.google.com/store/apps/details?id=com.abc.abcnews&reviewId=Z3A6QU9xcFRPRWZjREFaM3hwdFpSWVZWeUh0TXdJZU9uZ21YWlVYRVpRWUl2aG95SEhFZGQtVWZaTG1jeUNFU19TcUplS1hKaHVXeThVN2p4ZWVoWVprWmxN"><img
src="/assets/abc-news-app-negative-review.png" alt="ABC
News app negative review"></a><figcaption style="text-align: center">
Reviews like this, abundant on the Google Play store, discourage users
from downloading your app. </figcaption></figure>

User discontent often goes way beyond app deletion: a poor user experience
leads users to leave negative reviews on Google Play and discourages
consumers from downloading other apps from a given developer.  In fact,
[84% of users find app store ratings important when considering whether or
not to download an
app](https://info.dynatrace.com/rs/compuware/images/Mobile_App_Survey_Report.pdf).

In the web domain, developers have long known that performance is crucial
for success (e.g., Amazon saw that [an extra 100ms of latency could cost
up to 1% of
sales](http://highscalability.com/latency-everywhere-and-it-costs-you-sales-how-crush-it)). Mobile
developers have started to realize this only recently, but industry giants
are quickly catching on, devoting more time and resources to optimizing
their mobile apps.  They know it’s crucial to their success - that’s why
[Instagram developers spent a year profiling and optimizing their Android
app](http://instagram-engineering.tumblr.com/post/97740520316/betterandroid).
We analyzed four popular apps, Facebook, LinkedIn, Yahoo News Digest, and
WeChat, and found extensive performance monitoring code in all of
them. The message is universal: speed matters.

The take-home message is that your app’s performance is absolutely
important.  Fluid apps are essential to success in the mobile domain. Apps
that perform well engage and delight users, bring in positive reviews (and
with them, more customers), strengthen your brand, stand out in the
competition, and hopefully bring a little more money home :).
