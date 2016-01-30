---
layout: post
title: Note to Self - Regarding Apache on OSX Server
categories: webdevelopment
---
Note to Self - Remember the following when using Apache on a Mac with OSX Server:
[//]: #
<ul>
<li>The sites folder is at "<code>/Library/Server/Web/Data/Sites/</code>".</li>
<li>The server configuration is at "<code>/Library/Server/Config/apache2/</code>".</li>
<li>Set "<code>AllowOverride All</code>" in the "<code>/Library/Server/Config/apache2/sites/*.conf</code>" files.</li>
<li>Remove <p>"<code>SetEnvIf User-Agent ".*MSIE.*" nokeepalive ssl-unclean-shutdown</code>"</p> from "<code>/Library/Server/Config/apache2/http_server_app.conf</code>" as it is obsolete.</li>
<li>Restart the server using "<code>sudo apachectl restart</code>".</li>
</ul>