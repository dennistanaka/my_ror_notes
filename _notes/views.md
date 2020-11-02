---
title: Views
permalink: /notes/views/
---

<h4>Table of Contents</h4>
* TOC
{:toc}

## The Basics

### <head>

The default Rails layout includes lines like the below in its <head>:

{% highlight erb %}
<%= csrf_meta_tags %>
<%= stylesheet_link_tag ... %>
<%= javascript_include_tag "application", ... %>
{% endhighlight %}

And the method csrf_meta_tags prevents cross-site request forgery (CSRF), a type of malicious web attack.

### Provide and Yield

{% highlight erb %}
<% provide(:title, "Home") %>
<!DOCTYPE html>
<html>
  <head>
    <title><%= yield(:title) %> | Ruby on Rails Tutorial Sample App</title>
  </head>
  <body>
    <h1>Sample App</h1>
    <p>
      This is the home page for the
      <a href="http://www.railstutorial.org/">Ruby on Rails Tutorial</a>
      sample application.
    </p>
  </body>
</html>
{% endhighlight %}

#### <% ... %> vs <%= ... %>

<% ... %> executes the code inside, while <%= ... %> executes and inserts the results into the template.

Source: [Ruby on Rails Tutorial](https://www.railstutorial.org/book/static_pages)
