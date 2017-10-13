# Rails New and other basics

## Generate or Clone an application

### Generate a brand new application

`cd` to the folder where you want to store your new application. For me, this is `cd ~/workspace`. Then,

```bash
rails new my_fancy_app
```

This creates a subfolder called `my_fancy_app` and puts all of the boilerplate for a Rails application inside.

**For all subsequent commands, you must `cd` *in to* the application folder *first*; e.g. `cd my_fancy_app` from `~/workspace`.**

### Or if you cloned an existing application

`cd` in to the folder you just downloaded. Then,

```bash
bundle install
```

**The `bundle install` (or just `bundle` for short) command fetches all of the 3rd party Ruby code that the application depends upon and installs it on your machine. You only need to do this once per application.**

## Start the web server

On Cloud9,

```bash
rails server -b $IP -p $PORT
```

or on your own computer

```
rails server
```

(`rails s` is short for `rails server`, like `rails c` is short for `rails console`.)

If the server started successfully, you should see output like the following. It may take a moment.

```bash
=> Booting WEBrick
=> Rails 5.0.2 application starting in development on http://localhost:3000
=> Run `rails server -h` for more startup options
[2017-05-23 06:32:14] INFO  WEBrick 1.3.1
[2017-05-23 06:32:14] INFO  ruby 2.3.4 (2017-03-30) [x86_64-darwin16]
[2017-05-23 06:32:15] INFO  WEBrick::HTTPServer#start: pid=4618 port=3000
```
and then the cursor should be blinking at the bottom, but not at the end of your usual command prompt. This window is now dedicated to the web server app, and you can't run any other commands in it until you shut down the server.

If you need to run other command line stuff, open up a new window or tab.

### If the server failed to start

 1. If you got a "address already in use" error, then you must have an old `rails server` running in another window or tab somewhere. Find it and Ctrl-C (or just close the tab).
 2. If you have a syntax error in `config/routes.rb`, then the server will refuse to even start up. See if the error message complains about a line in that file.

## Shut down the web server

**Ctrl-C**. On Windows, you may be asked whether to terminate the job; say yes.

## Start the Rails Console

```bash
rails console
```

or `rails c` for short.

Rails Console is a superpowered version of IRB, handy for testing snippets of code.

## Set up the database

**If** the application you cloned requires database setup, then

    rails db:migrate
    
will create the tables and columns.

**If** I provided some starter dummy data for you, then

    rails dev:prime
    
will quickly pre-populate the tables for you, so you don't have to spend an hour in `rails console` adding rows.

## FAQ

#### I am getting an error relating to the pg gem when in bundle install

If your `bundle install` fails with a message about postgres or pgconfig, then

```bash
bundle install --without production
```

#### I am getting an error relating to ExecJS or `TypeError: Object doesn't support this property or method`

Go in to the `app/assets/javascripts/application.js` file and delete the line

    //= require_tree .

Refresh the page in Chrome; it should now be okay.

If you are still experiencing an error, try the following also:

 1. In `Gemfile`, delete the line 

        gem 'turbolinks'
 
 1. In `app/assets/javascripts/application.js`, delete the line

        //= require turbolinks

 1. `bundle install` and restart your server.