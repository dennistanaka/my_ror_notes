---
title: Basics
permalink: /notes/basics/
---

<h4>Table of Contents</h4>
* TOC
{:toc}

## Random Numbers and Leading Zero Formatting

{% highlight ruby %}
# generate random id based on current time and a random suffix
random_id = "#{Time.current.strftime('%H%M%S')}#{format('%06d', rand(0..999_999))}"

# format the generated id to fit in 13 characters (fill with leading zeros)
random_id = format('%013d', random_id.to_i)
{% endhighlight %}

Source: [StackOverflow](https://stackoverflow.com/questions/4395095/how-to-generate-a-random-number-between-a-and-b-in-ruby)
