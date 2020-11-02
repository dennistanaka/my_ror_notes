---
title: Development Environment
permalink: /notes/environment/
---

<h4>Table of Contents</h4>
* TOC
{:toc}

## Installation Guide

I never needed another guide for Rails installation:

[GoRails Install Guide](https://gorails.com/setup)

## Use Active Record MYSQL Encoding utf8mb4

[https://qiita.com/kamipo/items/101aaf8159cf1470d823](https://qiita.com/kamipo/items/101aaf8159cf1470d823)<br />
[https://qiita.com/xend/items/4d5c3333cbae53888f37](https://qiita.com/xend/items/4d5c3333cbae53888f37)


## Clean Gems Installed with Bundle

To remove gems installed system-wide:

{% highlight shell %}
$ bundle clean --force
{% endhighlight %}

To remove gems installed with --path:

{% highlight shell %}
$ bundle clean
{% endhighlight %}

Source: [GitHub Issue](https://github.com/bundler/bundler/issues/6648)

## Uninstall All Gems in the Current Environment

{% highlight shell %}
for i in `gem list --no-versions`; do gem uninstall -aIx $i; done
{% endhighlight %}

Source: [StackOverflow](https://stackoverflow.com/questions/4907668/removing-all-installed-gems-and-starting-over/13491563)
