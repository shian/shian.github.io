---
layout: post
published: true
title: 測試程式碼顯示效果
tags: test
date: 2014/03/03 10:00:00+08
---

* 內縮 4 格


    # Let me re-iterate ...
    for i in 1 .. 10 { do-something(i) }

* Markdown code block

~~~
define foobar() {
    print "Welcome to flavor country!";
}
~~~

* hexo code block

{% codeblock code block test lang:python %}
import time
# Quick, count to ten!
for i in range(10):
    # (but not *too* quick)
    time.sleep(0.5)
    print i
{% endcodeblock %}

* Gist

<iframe srcdoc='{% gist shian/f66363fd82e4a2edd89d %}' style="width:100%;height:100vh;"></iframe>




