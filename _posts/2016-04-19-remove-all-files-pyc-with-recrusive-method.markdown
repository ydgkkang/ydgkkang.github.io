---
layout: post
title:  "Remove all files .pyc with recrusive method"
date:   2019-06-28 14:39:34 +0700
categories: [react native]
---

맵위키 개발 로드맵 

{% highlight ruby %}
mapWiki/
           placeInfo
           instagram
           blogInfo
           livechat (socket.io)
{% endhighlight %}

Deleting the `.pyc` files one by one would be spending a lot of time. and you will be bored. There is sample how to handle it.

```
$ find your_dir -name *.pyc -delete
```

OR, if you work inside current directory.

```
$ find . -name *.pyc -delete
```
