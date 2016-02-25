---
layout: page
title: Documentation
permalink: /doc/
date: 2016-02-25
author: Nicolas Sebrecht
---

{% assign sources = site.data.links.imapfw.sources.master %}

* junk
{:toc}

# The Tao of imapfw

Here is the starting point to understand the global architecture about imapfw.

{:.note}
TIP: most of the file names are clickable.


## How the program boots

{:.note}
A top-down approach.

The Python file called from the command line is [`imapfw.py`]({{ sources }}/imapfw.py). Look at the imports:

{% highlight python %}
from imapfw import Imapfw
{% endhighlight %}

It first imports the [`imapfw` package]({{ sources }}/imapfw). As a good Python programer, you know that when importing a module of a package, Python first executes the `__init__.py` file(s) of this package (from high-level to down-level).

So here, it loads and executes [`imapfw/__init__.py`]({{ sources }}/imapfw/__init__.py). In this file, we have:

{% highlight python %}
from imapfw.init import Imapfw
{% endhighlight %}

Since `init` is in the same package, we can check this [`imapfw/init.py`]({{ sources }}/imapfw/init.py) out. Bingo! We have the starting code. Reading this file, you should figure that its job is to:

* initialize the environment;
* load and run the action requested at CLI.
