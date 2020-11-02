---
title: Pagination
permalink: /notes/pagination/
---

<h4>Table of Contents</h4>
* TOC
{:toc}

## Kaminari

### Total count of objects

{% highlight ruby %}
@object.total_count
{% endhighlight %}

### Current page

{% highlight ruby %}
@object.current_page
{% endhighlight %}

### Per page configured for the model

{% highlight ruby %}
@object.default_per_page
{% endhighlight %}

Source: [GitHub](https://github.com/kaminari/kaminari)
