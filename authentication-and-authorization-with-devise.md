# Authentication and Authorization with Devise

We will be using the [Devise gem][2] to help us get started with authentication (are you who you say you are?) and authorization (are you allowed to do/see this?).

## Add sign-in/sign-out

 - Add `gem 'devise'` to your Gemfile and `bundle`
 - `rails g devise:install`

Devise will give you some setup instructions. We don't need to worry about most of them, but we do need to set a root URL. Usually, you will point the root URL to the index action of some important resource in your application: In `config/routes.rb`:

```ruby
root 'photos#index'
```

> This is just a shortcut for setting a root URL the old way,

>     get "/", :controller => "photos", :action => "index"

Next, we need to secure one of our models with Devise. If you already have a model (like User) created, skip down to the "Add Devise for existing model" section. Otherwise continue with the "Generate a new model with Devise" section. 

### Generate a new model with Devise

Use the following command to generate a User model with Devise built-in. Replace the column names with ones that are relevant to your application. 

```bash
rails g draft:devise user username:string avatar_url:string
```

`rake db:migrate` and restart your server.

### Add Devise for existing model

**Skip down to "benefits" if you've already generated a new model with Devise. You don't need to do both.**

If you already have rows in the users table and don't want to drop your database, you will have to go through a couple of extra steps to prevent errors.

 - First, add a column called "email" if you don't already have one.
 - Second, make sure that every existing row has a unique value for email.

    Then,

        rails g draft:devise user

 - Finally, go into the migration file called "add_devise_to_users" and comment out the line that adds an email column.

    and

        rails db:migrate

    and restart your server.

## Benefits

The big benefits that we now get for free from Devise are:

 - RCAVs that handle sign up, sign in, and sign out -- all done, for free!
 - **the `current_user` helper method, available within all views and controllers, that will retrieve the row from the Users table for whoever is currently signed in**
 - the `before_action :authenticate_user!` filter that we can use in our controllers to ensure someone is signed in before accessing any actions within that controller

There are lots more (password reset emails, etc), but these are the first ones that we care about.

The application layout file that is written by `rails g starter:style default` includes examples in the nav bar of what the sign-up/in/out links look like. You'll have to customize them a bit based on what you called your secure model. **Notice the `data-method="delete"` attribute on the sign-out link -- that is important, and you need to include it.** (But be careful not to include it on regular links if you, e.g., copy-paste this one.)

## Customizing Devise Views

Devise does an incredible amount of work for us out of the box, but at some point, we will want to customize it; at the very least, we will want to make the sign-up and sign-in forms look nicer.

Assuming we are using `before_action :authenticate_user!` in our `ApplicationController` to force visitors to sign up or sign in before doing anything else, then the sign in page is our landing page, after all (try going to Twitter, Facebook, etc when signed out -- the landing page is really a sign-in page with some extra info thrown in). So it would be nice to be able to make it pretty.

More importantly, we will likely want to allow users to provide more information when they sign up or edit their profiles than simply their email addresses and passwords.

### Step One: Get Our Hands On The View Templates

The first problem is that we don't even have any code to edit in order to customize the view templates for sign-in, sign-up, edit profile, etc. That's because, by default, these templates are wrapped up inside the Devise gem.

It's really easy to have Devise generate copies of these templates that we can edit, though. And then our edited versions will take precedence. Simply run

```bash
rails g devise:views
```

There will now be a folder in your `app/views` folder called `devise`, with a whole bunch of stuff in it. What we are most interested in are the contents of the `registrations` and `sessions` subfolders. `app/views/devise/registrations/new.html.erb` is the sign up form, `registrations/edit.html.erb` is the edit profile form, and `sessions/new.html.erb` is the sign in form.

### Step Two: Modify The Markup

Devise's markup is a bit more advanced than what we had time to get to in class. We have, until now, only been writing raw HTML code by hand.

In practice, Rails developers often use built-in Ruby helper methods to generate HTML. This provides benefits in terms of security, brevity, etc.

Devise is using some of these helpers to draw the `<form>` and `<input>` elements in its forms, so we don't directly see those things in the view templates.

Instead, we see something like

```erb
<%= form_for(resource, as: resource_name, url: registration_path(resource_name)) do |f| %>
  <%= devise_error_messages! %>

  <div><%= f.label :email %><br />
  <%= f.email_field :email, autofocus: true %></div>

  <div><%= f.label :password %><br />
    <%= f.password_field :password %></div>
```

etc. Basically, the `form_for` helper method is spitting out the `<form>` tag, and each of the `f.____field` methods are spitting out the `<input>` tags.

#### Add HTML Around The Helpers

You can write whatever HTML you want *around* these helpers; for example, Devise has already wrapped each label/input pair inside a `<div>`.

If we're adhering to [Bootstrap conventions for form markup][1], we should probably add `class="form-group"` to each of those. Also, we should remove the `<br />` tags that Devise includes.

#### Add CSS Classes To The Helpers

You can also add CSS classes to the input tags they generate, like so:

```erb
<%= f.password_field :password, :class => "form-control" %>
```

#### Add Additional Input Helpers
    
There are various types of `____field` helpers; the most common are

 - `f.text_field`
 - `f.email_field`
 - `f.password_field`
 - `f.number_field`
 - `f.check_box`
 - `f.collection_select` -- this one is special. It is similar to the `select_tag` and `options_from_collection_for_select` helpers we discussed in class, but rolled into one. The syntax looks like this (assuming you have a Company table and you want the user to belong to one company):

        <%= f.collection_select :company_id, Company.all, :id, :name %>

You can add as many of these as you need for the additional columns you've included in your user model.

#### Example Bootstrapped Devise Forms

[Here are some examples of the Devise forms customized with Bootstrap classes.](https://github.com/firstdraft/bootstrapped_devise_forms) You can copy-paste them into your `app/views/devise/` folder to use as a starting point, if you wish.

### Step Three: Allow Additional Parameters Through Security

The last step we need to take is to whitelist these additional attributes as things that we will allow users to modify about themselves. To do this, you need to go to your `ApplicationController` and add the following code:

```ruby
class ApplicationController < ActionController::Base
  before_action :configure_permitted_parameters, if: :devise_controller?
  
  def configure_permitted_parameters
    devise_parameter_sanitizer.permit(:sign_up, :keys => [:username, :avatar_url])
    
    devise_parameter_sanitizer.permit(:account_update, :keys => [:avatar_url])
  end
end
```

You need to add the name of each column you want to be able to modify to the respective array of symbols. In the example, I have whitelisted both username and avatar_url to be modified upon sign-up, but only avatar_url can be modified upon account update. You have to decide what makes sense in your app.

  [1]: http://getbootstrap.com/css/#forms
  [2]: https://github.com/plataformatec/devise
