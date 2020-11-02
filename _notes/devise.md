---
title: Devise
permalink: /notes/devise/
---

<h4>Table of Contents</h4>
* TOC
{:toc}

## Create an User Manually in the Console

{% highlight ruby %}
user = User.new(email: 'my_email@my_domain.com', password: 'my_password', password_confirmation: 'my_password')
user.save
{% endhighlight %}

Source: [StackOverflow](https://stackoverflow.com/questions/4660565/how-to-manually-create-a-new-user-and-user-session-in-devise)

## Helpers

### after_sign_in_path_for

`after_sign_in_path_for` defines the default url to be used after signing in and can be easily overwritten.

I see it being used, for example, to set session variables needed after sign in.

Source: [Devise Documentation](http://www.rubydoc.info/github/plataformatec/devise/Devise/Controllers/Helpers:after_sign_in_path_for)
