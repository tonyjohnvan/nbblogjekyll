---
layout: post
title:  "Slow Android Reflection"
author: antonkrasov
comments: true
name: "slow"
lang: "English"
visible: true
---

<!-- Before even entering the realm of android development, many developers have experience in the Java world. As a result, they become comfortable with Java libraries like [Jersey](https://jersey.java.net/){:target="_blank"}. -->

Reflections are, of course, an extremely useful aspect of Java and Android development. Yet it turns out that reflection, when used incorrectly, can very often be the source of significant slowdown within an Android application. Perhaps the most intuitive way of understanding this is going through a real life example. Take a look at Nimbledroid's profile for [Photobucket](https://nimbledroid.com/play/com.photobucket.android?p=2DGhhgjWGOFDjP#Icicle%20Graph){:target="_blank"}, a large photo-sharing platform.

<figure><img src="{{ site.baseurl }}/assets/slow-android-reflection/com.photobucket.android-iricle-graph-top.png" alt="com.photobucket.android Iricle Graph" /></figure>

We see that the <code>com.photobucket.api.client.jersey.UserClient</code> contractor takes an entire 660ms to create. Looking further into the icicle graph, we see that the reason for such a lag lies in reflection. Check this out:

<figure><img src="{{ site.baseurl }}/assets/slow-android-reflection/com.photobucket.android-iricle-graph-bottom.png" alt="com.photobucket.android Iricle Graph" /></figure>

Note that the [getGenericInterfaces() method](http://developer.android.com/reference/java/lang/Class.html#getGenericInterfaces()){:target="_blank"} returns the types of the interfaces that this Class directly implements. Here, it is invoked 5 times and takes ~81ms. Sure, on the surface, this may not seem like much, but altogether, use of the method is causing ~600ms of start time delay. Let's take a deeper look at why this is taking so long.

It turns out that this library allows developers to configure a REST client with annotations. The issue is that the library doesn't process the annotations during build time, but instead parses and creates the REST client during runtime (with the help of reflection). From a performance point of view, this is catastrophic.

We've created a [simple test](https://gist.github.com/antonkrasov/7664b926966b9bb363eb){:target="_blank"} to verify how slow reflection is.


We will work with android.app.Activity class and repeat operations 10,000 times, like this:
{% highlight java %}
Class<?> clazz = android.app.Activity.class;
for (int i = 0; i < 10000; i++) {
	clazz.getFields();
}
{% endhighlight %}

We've also set up two tests that include creating objects (of the type DummyItem, an empty dummy class) to look at the overhead purely caused by reflection. Here's the example:

{% highlight java %}
try {
    for (int i = 0; i < 1_000_000; i++) {
        DummyItem.class.newInstance();
    }
} catch (InstantiationException e) {
    e.printStackTrace();
} catch (IllegalAccessException e) {
    e.printStackTrace();
}
{% endhighlight %}


And here are our results:

<figure><img src="{{ site.baseurl }}/assets/slow-android-reflection/table.png" alt="com.photobucket.android Iricle Graph" /></figure>

It's evident that creating objects is excruciatingly slow via reflection (compare the 2891ms and 6384ms with reflection to the 774ms and 358ms without reflection).


#### **One more example**

[ActiveAndroid](http://www.activeandroid.com){:target="_blank"} is another library that uses reflection. Let's take a look at how it can affect start time:

[Scribd](https://nimbledroid.com/play/com.scribd.app.reader0?p=2DGmfF1rC8PO85#Icicle%20Graph){:target="_blank"} app

<figure><img src="{{ site.baseurl }}/assets/slow-android-reflection/Scribd.png" alt="Scribd Iricle Graph" /></figure>

[Myntra](https://nimbledroid.com/play/com.myntra.android?p=2MaFbQjkB3NqbR#Icicle%20Graph){:target="_blank"} app

<figure><img src="{{ site.baseurl }}/assets/slow-android-reflection/Myntra.png" alt="Myntra Iricle Graph" /></figure>

As you can see, the library requires more than a second to initialize. That's a lot of time, especially taking into consideration that [users expect an average app start time of 2s](http://blog.nimbledroid.com/2015/09/03/why-you-should-care-about-app-performance.html).
