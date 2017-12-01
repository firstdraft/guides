# Deploying to Heroku

 1. Sign up for a [Heroku account](https://www.heroku.com/) if you haven't already.
 
 1. At a Terminal prompt, run the command `heroku login`:
 
    ![](/assets/heroku login.png)
    
 1. To get the app ready to deploy to Heroku, ensure the following:
 
    - In your `Gemfile`, look for a line that says:
    
       ```ruby
       gem "sqlite3"
       ```
        
       If you have it, it should be modified to:
        
       ```ruby
       gem "sqlite3", :group => :development
       ```
       
       or
       
       ``` ruby
       group :development do
         gem "sqlite3"
       end
       ```
       
       and, in addition, add the line
       
       ```ruby
       gem "pg", :group => :production
       ```
       
       or
       
       ```ruby       
       group :production do
         gem "pg"
       end
       ```
       
       This step may already be done for you, depending on which project you're working on. We're now ready to use the powerful database that Heroku provides[^1].

    - In your `Gemfile`, look for a line that says:
    
       ```ruby
       gem "rails_12factor", :group => :production
       ```

       If you don't have it, add it. Alternatively, you could have something like this[^2]:
       
       ```ruby
       group :production do
         gem "pg"
         gem "rails_12factor"
       end
       ```
       
    - If you made any changes to your `Gemfile`, then `bundle install` commit the changes to `master`.              



[^1]: Heroku gives us a very powerful open-source database called Postgres. By default, a brand new Rails application uses a lightweight database called SQLite since it is already installed on basically every device that exists. We have to ensure that we make our app compatible with Postgres. Fortunately, since ActiveRecord handles translating our Ruby into SQL for us anyway, this requires no change to our application code. We simply need to switch to a different adapter when Heroku starts up the `rails server` in production mode (as opposed to development mode, which is what we do on our own machine).

[^2]: Any gems that are listed within the `:production` group will only be used when the `rails server` is started up in production mode. Usually, we start our server in the default mode, which is `development`. If you really wanted to, you could also restrict other gems to the `:development` group if they aren't used while serving actual requests; for example, `starter_generators`. This will result in a (small) performance boost.

