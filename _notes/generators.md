---
title: Generators
permalink: /notes/generators/
---

<h4>Table of Contents</h4>
* TOC
{:toc}

## Generated Content

### rails generate model

**Usage:**

{% highlight shell %}
$ rails generate model NAME [field[:type][:index] field[:type][:index]] [options]
{% endhighlight %}

**Description:**

Stubs out a new model. Pass the model name, either CamelCased or under_scored, and an optional list of attribute pairs as arguments.

Finally, if `--parent` option is given, it's used as superclass of the created model. This allows you create Single Table Inheritance models.

If you pass a namespaced model name (e.g. admin/account or Admin::Account) then the generator will create a module with a table_name_prefix method to prefix the model's table name with the module name (e.g. admin_accounts)

**Available field types:**

* integer
* primary_key
* decimal
* float
* boolean
* binary
* string
* text
* date
* time
* datetime

**Example:**

{% highlight shell %}
$ rails generate model account
{% endhighlight %}

For Active Record and TestUnit it creates:

Model:      app/models/account.rb
Test:       test/models/account_test.rb
Fixtures:   test/fixtures/accounts.yml
Migration:  db/migrate/XXX_create_accounts.rb

### rails generate controller

{% highlight shell %}
$ rails generate controller NAME [action action] [options]
{% endhighlight %}

**Description:**

Stubs out a new controller and its views. Pass the controller name, either CamelCased or under_scored, and a list of views as arguments.

To create a controller within a module, specify the controller name as a path like 'parent_module/controller_name'.

This generates a controller class in app/controllers and invokes helper, template engine, assets, and test framework generators.

**Example:**

{% highlight shell %}
$ rails generate controller CreditCards open debit credit close
{% endhighlight %}

CreditCards controller with URLs like /credit_cards/debit.

Controller: app/controllers/credit_cards_controller.rb
Test:       test/controllers/credit_cards_controller_test.rb
Views:      app/views/credit_cards/debit.html.erb [...]
Helper:     app/helpers/credit_cards_helper.rb

Source: rails generate command help

## References

Consider the following User model:

{% highlight shell %}
$ rails g model User name:string
{% endhighlight %}

The command above generates the following migration:

{% highlight ruby %}
class CreateUsers < ActiveRecord::Migration[5.0]
  def change
    create_table :users do |t|
      t.string :name

      t.timestamps
    end
  end
end
{% endhighlight %}

We can use user:references to define a foreign key:

{% highlight shell %}
$ rails g model Post user:references body:text
{% endhighlight %}

What generates the migration below:

{% highlight ruby %}
class CreatePosts < ActiveRecord::Migration[5.0]
  def change
    create_table :posts do |t|
      t.references :user, foreign_key: true
      t.text :body

      t.timestamps
    end
  end
end
{% endhighlight %}

It automatically names the corresponding column user_id and adds an index on it.

The command below generates the exactly same table schema in the case of SQLite:

{% highlight shell %}
$ rails g model Post user_id:integer:index body:text
{% endhighlight %}

But the migration file is different:

{% highlight ruby %}
class CreatePosts < ActiveRecord::Migration[5.0]
  def change
    create_table :posts do |t|
      t.integer :user_id
      t.text :body

      t.timestamps
    end
    add_index :posts, :user_id
  end
end
{% endhighlight %}

When using references, rails automatically adds the line below to the Post model:

{% highlight ruby %}
belongs_to :user
{% endhighlight %}

But the user has to be modified manually.

Source: [sitepoint](https://www.sitepoint.com/brush-up-your-knowledge-of-rails-associations/)

### Migration API in Rails 5

In Rails 5, when we reference a model, an index on the foreign_key is automatically created. As we want indexes for referenced columns in almost all cases, Rails 5 does not need references to have index: true. When migrations are run then index is automatically created.

Source: [StackOverflow](https://stackoverflow.com/questions/39769981/why-did-rails-5-changed-index-to-foreign-key)

## Dependent



## Generators Hangs When Executed

Suppose we execute a scaffolding command like the below:

{% highlight shell %}
$ rails generate scaffold User name:string email:string
{% endhighlight %}

And the command hangs and freezes the command-line. It should happen with other generators as well and it is caused by issues in the generated binstubs of rails. To reset the binstubs, we have to delete the ```/bin``` folder and execute the command below (Rails 5 on):

{% highlight shell %}
$ rake app:update:bin
{% endhighlight %}

Source: [StackOverflow](https://stackoverflow.com/questions/31857365/rails-generate-commands-hang-when-trying-to-create-a-model)

## Cancel Generate Command Output

Sometimes we want to cancel the results of the generate command. We can do this by using the destroy command. For example, these two commands cancel each other out:

{% highlight shell %}
$ rails generate controller StaticPages home help
$ rails destroy  controller StaticPages home help
{% endhighlight %}

Other examples:

{% highlight shell %}
$ rails generate model User name:string email:string
$ rails destroy model User
{% endhighlight %}

Source: [Ruby on Rails Tutorial](https://www.railstutorial.org/book/static_pages)

## Migrations for Common Database Operations

### Drop Table

{% highlight ruby %}
drop_table :table_name
{% endhighlight %}

### Remove Foreign Key

{% highlight ruby %}
remove_foreign_key :table_name, :referenced_table_name
{% endhighlight %}

### Remove Index

{% highlight ruby %}
remove_index :table_name, name: 'index_name'
{% endhighlight %}

Source: [Rails Guide](https://edgeguides.rubyonrails.org/active_record_migrations.html)
