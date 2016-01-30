---
layout: post
title: Fix for Old Browsers
categories: webdevelopment
---
Supporting older browsers, in particular old Internet Explorer versions, can be very difficult and takes a lot of time and effort.
If you agree with that statement, then I suggest you add the following rule to the .htaccess file of your Apache site.
[//]: #
<br><br>
{% highlight css %}
<IfModule mod_rewrite.c>
  RewriteEngine on
  RewriteCond %{HTTP_USER_AGENT} MSIE\ ([5678])\.
  RewriteRule .* http://www.browser-update.org/update.html [R=302,L]
</IfModule>
{% endhighlight %}
<br><br>
It will make your life better and the world a better place!<br>
Visit <a href="http://bracke.dk">bracke.dk</a> with an old IE version to get a demo.