---
layout: post
title: Fix Bonobo Problem
categories: Bonobo Git
---
How to fix 'protocol error: bad line length character: &lt;!DO' problem with the Bonobo Git Server.
<!--more-->

### The Problem
When I push changes to a project on the Bonobo Git server, it fails with the following message:

```bash
protocol error: bad line length character: <!DO
```

It only happens with large commits.


### The Solution
The problem is the resulting size of the request. There is a max size and when that is reached it results in apartial request.

The solution is to increase the max request size in the Bonobos web.config:

```xml
<httpRuntime maxRequestLength="2147483647" />
```

