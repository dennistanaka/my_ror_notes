---
title: Testing
permalink: /notes/testing/
---

<h4>Table of Contents</h4>
* TOC
{:toc}

## The Basics

### A Typical Test

{% highlight ruby %}
require 'test_helper'

class StaticPagesControllerTest < ActionDispatch::IntegrationTest

  def setup
    @base_title = "Ruby on Rails Tutorial Sample App"
  end

  test "should get home" do
    get static_pages_home_url
    assert_response :success
    assert_select "title", "Home | #{@base_title}"
  end

  test "should get help" do
    get static_pages_help_url
    assert_response :success
    assert_select "title", "Help | #{@base_title}"
  end

  test "should get about" do
    get static_pages_about_url
    assert_response :success
    assert_select "title", "About | #{@base_title}"
  end
end
{% endhighlight %}

Run with:

{% highlight shell %}
$ rails test
{% endhighlight %}

Source: [Ruby on Rails Tutorial](https://www.railstutorial.org/book/static_pages#sec-adding_page_titles)
