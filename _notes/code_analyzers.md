---
title: Code Analyzers
permalink: /notes/code_analyzers/
---

<h4>Table of Contents</h4>
* TOC
{:toc}

## Introduction

Code analyzers are a valuable tool, especially when working on a team of developers, as they help keep the code's style uniform throughout the development process.

## Rubocop

From the website:

> RuboCop is a Ruby static code analyzer and code formatter. Out of the box it will enforce many of the guidelines outlined in the community Ruby Style Guide.

Installing it is a matter of adding the following line to the development section of a Gemfile:

{% highlight ruby %}
gem 'rubocop', require: false
{% endhighlight %}

It's desirable to stick to a certain version as there are frequently incompatibilities between versions:

{% highlight ruby %}
gem 'rubocop', '~> 0.58.2', require: false
{% endhighlight %}

Running it is a matter of using the following commands:

{% highlight shell %}
$ cd my/cool/ruby/project
$ rubocop
{% endhighlight %}

It comes with a set of defaults that can the configured to fit your project's needs. Just add a ```.rubocop.yml``` file to your project's root. An example file can be found in Rubocop's GitHub:

[https://github.com/rubocop-hq/rubocop/blob/master/.rubocop.yml](https://github.com/rubocop-hq/rubocop/blob/master/.rubocop.yml)

## scss-lint

A SCSS analyzer. To install it, just add the following line to the development section of a Gemfile:

{% highlight ruby %}
gem 'scss_lint', require: false
{% endhighlight %}

We can run it with the following command. The folder will be recursively scanned.

{% highlight shell %}
$ scss-lint app/assets/stylesheets/
{% endhighlight %}

We can configure it to suit our needs by placing a .scss-lint.yml file in our project's root. Details about its syntax can be found in the link below:

[https://github.com/brigade/scss-lint#configuration](https://github.com/brigade/scss-lint#configuration)

## slim-lint

A Slim file analyzer. To install it, just add the following line to the development section of a Gemfile:

{% highlight ruby %}
gem 'slim_lint', require: false
{% endhighlight %}

We can run it with the following command. The folder will be recursively scanned for .slim files.

{% highlight shell %}
$ slim-lint app/**/*.slim
{% endhighlight %}

We can configure it to suit our needs by placing a .slim-lint.yml file in our project's root. Details about its syntax can be found in the link below:

[https://github.com/sds/slim-lint#configuration](https://github.com/sds/slim-lint#configuration)

