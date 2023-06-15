---
author: chrisbeeley
categories:
- Uncategorized
date: "2015-11-18T18:36:25Z"
guid: http://chrisbeeley.net/?p=783
id: 783
title: G++ error compiling on R
url: /?p=783
---

I was installing R packages (the httpuv package, but I imagine others would generate the same problem) on my Ubuntu server today and I got a very strange error message:

g++: error: Welcome: No such file or directory  
g++: error: to: No such file or directory  
g++: error: R!: No such file or directory

It was a problem with my .Rprofile.site file. That’s why it looks funny, because R is saying “Welcome to R”, but for some reason this is messing with g++. In my case it seemed to be generated by running R as sudo, but I need to do that to make the package library writable. Just invoke R at the terminal with:

```
<pre class="brush: bash; title: ; notranslate" title="">

R --no-site-file

```

and it will be fixed.