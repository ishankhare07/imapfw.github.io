---
layout: post
title: Leveraging third services in open source
date: 2016-03-04
author: Nicolas Sebrecht
categories: website project
---

Github ecosystem is growing. I decided it was time to make use of two more
promising services from the integrated tools.

<!-- more -->

* junk
{:toc}

# Introduction

Interesting changes happen! We are currently in a move to more integration
between online services. Of course, this is not something new because the
technology is there and it is used since quite some time. IMHO, what is changing
is that more and more **small teams** coming from open source communities **are
making their way in this economy while still featuring FOSS**.

Leveraging them is a good thing for most open source projects. Even fresh
starting projects like imapfw can seriously benefit from the tools they provide.

Here are those I enabled. Select the best tools is not hard as long as you know
what you want. My mandatory criteria for this project are:

* clear limitations regarding the free services they provide;
* as much as open source code as possible;
* **not going to become captive and locked into closed products**: we must
  always own our work and be able to easily move to something else if required.


# Travis CI

[Travis CI](https://travis-ci.org) was the first I enabled. Their intend to keep
working with open source communities looks **real and effective**.

Development is using continous integration for both our `master` and `next`
branches. One feature I like most is the possiblity to have *pull requests*
automatically fetch and run in the testing environment with seamless feedback
into github. That's awesome!

Thank you much guys!


# Gitbook

[Gitbook](https://www.gitbook.com/) will be used for [our documentation]({{
site.data.links.imapfw.doc }}).

All the members in the official team will be able to edit the documentation
online.  That's a big plus because **documentation is key** for a framework. The
more it's easy to make changes, the more we'll likely have improvements.

Also, anyone with a Github, Facebook, Google or Twitter account can leave inline
comments to the authors while browsing the documentation online.

Thanks Gitbook!

# Gitter

[Gitter](https://gitter.im) is a service for "chatting". We have [our own
room](https://gitter.im/OfflineIMAP/imapfw) there.

To be honest, I've heard complaints *(on IRC...)* about this kind of service. I
do think most of them miss the point. What's wonderful is not only what Gitter
provides today (and how easy it can be compared to IRC) but all the awesome
stuff they can potentially enable in the future. Please, don't make yourself
strong opinions from your own perspective and requirements! There are a lot of
ways they can benefit to others, including open source communities.

So yes, I do think they are doing a fucking good job. If I've put "chatting"
within quotes above it's because Gitter's chat is far more than just that. Logs
are persistent, desktop and mobile clients are available, markdown and a lot of
fancy tricks are supported: desktop notifications, fixing typos in text already
sent with `s/error/fix it/`, etc.

> Check out the bottom right button. ,-)

Integrating Gitter into this website has been so easy!

Thank you Gitter! Keep up the good work!


# Final note

I remember back in the old days when enabling all those kind of features was
hard if not simply impossible for small projects like imapfw...  Projects had
websites with ugly colors and fonts, sending simple changes used to request lot
of work and strong implication into the project, advanced features like
continous intergration required spending your own money into infrastructures,
etc.

If there is one area for which the *"good old days"* does not envy me anymore,
it's probably this one.

***We are entering a new age with good, embrace it!***
