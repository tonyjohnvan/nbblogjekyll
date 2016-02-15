---
layout: post
title:  "NimbleDroid Product Update, Feb 2016"
author: josh
comments: true
name: "update 1"
lang: "English"
visible: true
mainpic:
youMayAlsoLike: "fluid app"
tags:
    - Development
    - Technology
    - Android
    - Optimization
    - Software
imageUrl: assets/febupdates/feb_insight.png
categories: en post
category: Development
---

We’ve been hard at work over the past few weeks making NimbleDroid an even more powerful tool for Android developers seeking to improve the performance of their apps. In this post we’ll discuss some of the biggest changes we’ve made in this update, and then offer a quick preview of what to expect moving forward.

### **Even More App Insight**

NimbleDroid has always provided detailed analysis of an app’s speed and responsiveness, but in talking with our users we realized that there’s even more that we can do to help developers understand the inner workings of their apps. This is especially true of items that will affect performance on older or less powerful devices.

As a result, we’re pleased to introduce new measurements for **memory usage**, **network usage**, **disk i/o**, **file size**, and **method count** to all NimbleDroid profiles. Zero extra work is needed on the part of the user - we simply calculate the data as we analyze the uploaded apk. Developers can now explore detailed summaries of method count and file size that will help them better understand which libraries contribute most to the 65k method limit and which asset files make their apps substantially larger. Expect even more information to come in future versions!

<figure><img
src="/assets/febupdates/feb_insight.png" alt="New Available App Information" style="margin: 0 auto"><figcaption style="text-align: center">
Access brand new data </figcaption></figure>

<figure><img
src="/assets/febupdates/feb_methodcount.png" alt="Method Count Graph" style="margin: 0 auto"><figcaption style="text-align: center">
Go into more detail </figcaption></figure>

### **Scenario Profiling**

At NimbleDroid, we made Cold Startup the focus of our initial features because it’s the first experience a user has with an app. But we know that the majority of time invested by developers and users is spent on an app’s functionality after startup. That’s why we’re excited to announce that we now provide automated identification and **analysis of other actions** in apps! Again, **no manual definition is needed**. We crawl through the app looking for actions, and then report the same measurements that we do for Cold Startup. We currently identify certain actions on the start screen, and we’ll soon be profiling even more scenarios.

<figure><img
src="/assets/febupdates/feb_scenario.png" alt="Scenario Example"><figcaption style="text-align: center">
New scenario profiling </figcaption></figure>

### **Sharing**

As NimbleDroid’s usership has expanded, we’ve seen a growing desire from users to be able to share results with members of their team or with the public. Until now, this could only be done by sharing a login or taking screenshots, so we’re happy to present new **team and public sharing capabilities** that will make sharing profiles much simpler. Users can now reveal results for a specific upload to the public, or give specific team members access to all of an app’s existing and new results.

<figure><img
src="/assets/febupdates/feb_sharing.png" alt="New Sharing Capabilities"><figcaption style="text-align: center">
Share with the public or with individuals </figcaption></figure>

### **Slack Notifications**

Since many users have already taken advantage of NimbleDroid’s ability to integrate with their CI process, we thought it might be helpful to notify them when new uploads are done profiling. To that end we’ve added Slack notifications to our feature list - NimbleDroid will now post a **Slack message when a new profile is ready**. We’re currently working on improving the content of notifications to give greater insight into what new issues have been introduced since the previous profile.

<figure><img
src="/assets/febupdates/feb_slack.png" alt="Notification from Slack" style="margin: 0 auto"><figcaption style="text-align: center">
Get notifications directly in Slack </figcaption></figure>

### **Looking Forward**

We have some exciting plans for upcoming features, including email notifications, more comprehensive Scenario coverage, and reporting/monitoring of diffs across versions. As well as a few secret projects that we can’t divulge just yet!  

Thanks for reading, and if you have any ideas or requests for features, please drop us a line at [contact@nimbledroid.com](mailto:contact@nimbledroid.com).
