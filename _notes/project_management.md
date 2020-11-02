---
title: Managing Rails Projects
permalink: /notes/projects/
---

<h4>Table of Contents</h4>
* TOC
{:toc}

## Skip 'bundle install' on New Projects

Use the option ```--skip-bundle```

{% highlight shell %}
$ rails new project_name --database=mysql --skip-bundle
{% endhighlight %}

Source: [StackOverflow](https://stackoverflow.com/questions/46179835/how-to-go-about-creating-rails-app-without-running-bundle-install)

## Rails Application in the Current Directory

{% highlight shell %}
$ rails new .
{% endhighlight %}

Source: [Jason Meridth Blog](https://blog.jasonmeridth.com/posts/create-rails-application-in-current-directory/)

## Project Setup

### Disable turbolinks in Rails 5

1. Remove the `gem 'turbolinks'` line from your Gemfile.

2. Remove the `//= require turbolinks` from your app/assets/javascripts/application.js.

3. Remove the two `"data-turbolinks-track" => "reload"` hash key/value pairs from your app/views/layouts/application.html.erb.

Source: [StackOverflow](https://stackoverflow.com/questions/38649550/how-to-disable-turbolinks-in-rails-5)
