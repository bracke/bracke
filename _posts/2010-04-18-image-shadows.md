---
layout: post
title: Image Shadows
categories: webdevelopment
---
I have looked into improving the way images are presented in my blog. I want them to have a shadow, without having to change the pictures.
[//]: #
<br><br>Helpfully the new CSS3 has the box-shadow feature which is just what I need. Obviously things aren&#8217;t that simple, since the browser support for box-shadow is limited. Instead I have used the following concoction:<br><br>

{% highlight css %}
img {
 box-shadow: 3px 3px 3px #666;
 -moz-box-shadow: 3px 3px 3px #666;
 -webkit-box-shadow: 3px 3px 3px #666;
 filter: progid:DXImageTransform.Microsoft.dropShadow(color=#666, offX=3, offY=3, positive=true);
}
{% endhighlight %}

<br><br>This should make sure all pictures will get a shadow no matter what browser is used to display them.