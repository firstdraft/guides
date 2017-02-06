# `starter_generators`

Include this in `Gemfile`, which is a file located in the root folder of your app:

```ruby
# Gemfile

gem "starter_generators", :git => "https://github.com/raghubetina/starter_generators.git"
```

Then, 

```bash
bundle install
```

## Resources

To generate a complete, database-backed web resource:

```bash
rails generate starter:resource <MODEL_NAME_SINGULAR> <COLUMN_1_NAME>:<COLUMN_1_DATATYPE> <COLUMN_2_NAME>:<COLUMN_2_DATATYPE> # etc
```

For example,

```bash
rails generate starter:resource photo source:string caption:text
```

 - The model name must be singular. 
 - Separate column names and datatypes with colons (NO SPACES).
 - Separate name:type pairs with spaces (NO COMMAS).

Note: `rails g` is short for `rails generate`, like `s` for `server` and `c` for `console`.

`rails db:migrate` to run the migration that the generator wrote for us to create the new table.

> #### If you generated something mistaken:

>  - and you already  `rake db:migrate`d, first

>         rake db:rollback

>     to undo just the most recent migration. If you didn't `rake db:migrate` after you generated the resource, then no need to do this step.

>  - **Next**,

>         rails destroy starter:resource photo

>     will remove all the files that it previously added. You can then re-generate from scratch.

## Application Layout

To generate an application layout file that includes links to Bootstrap, Font Awesome, and some boilerplate markup for a nav bar and alert messages, run the command

    rails g starter:style <THEME>

`<THEME>` can either be `default`, or the name of any [Bootswatch][1] (downcase), e.g., `cerulean`.

It will warn you that it is going to overwrite your existing `application.html.erb` -- say yes if you are sure that's okay. Copy out any important stuff if necessary, to be re-pasted back in.

### FAQ

#### I am getting an error relating to SSL when I `bundle`

If your `bundle install` fails with a message like this:

```bash
Gem::RemoteFetcher::FetchError: SSL_connect returned=1 errno=0 state=SSLv3 read server certificate B: certificate verify
```

then open the file called `Gemfile` in the root folder of the application with Sublime and change

    source 'https://rubygems.org'

to

    source 'http://rubygems.org'
    
(remove the "s"). Save and then `bundle install` again.

This is only a temporary fix. Long term, you should find [a permanent solution](https://gist.github.com/luislavena/f064211759ee0f806c88) or switch to a different development environment (Linux, OS X, or a cloud environment like [Nitrous.io](https://pro.nitrous.io/) or [Cloud9](https://c9.io/)).

#### I am getting an error relating to ExecJS

Go in to the `app/assets/javascripts/application.js` file and delete the line

    //= require_tree .

Refresh the page in Chrome; it should now be okay.

If you are still experiencing an error, try the following also:

 1. In `Gemfile`, delete the line 

        gem 'turbolinks'
 
 1. In `app/assets/javascripts/application.js`, delete the line

        //= require turbolinks

 1. `bundle install` and restart your server.


  [1]: http://bootswatch.com