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

 1. Run the command:
 
     ```
     heroku create your-app-name-production --remote=production
     ```
     
     replacing `your-app-name` with a name of your choice[^3].
     
 1. Run the command:
 
     ```
     git push production master
     ```
     
     ![](/assets/git push production master.png)

 1. What just happened? First, we set up another remote location _besides GitHub_ that we can `git push` our code to, and named it `production`. That second remote location is on one of Heroku's servers[^5], rather than one of GitHub's[^4].
 
     GitHub's purpose in life is to safely store your Git repositories, and also give you a bunch of tools to discuss and collaborate on it. It's sort of like a super-powered Dropbox-for-code.
     
     Heroku's purpose in life is simple — to receive your code and run it! You'll notice that it's doing the same thing that you would have done to start up the `rails server` after cloning the project — `bin/setup`, `bundle install`, etc:
     
     ![](/assets/bundling.png)
     
     Eventually, it will complete and tell you that it has deployed the application to a public URL, `https://[YOUR APP NAME]-production.herokuapp.com/`[^6]:
     
     ![](/assets/deployed.png)

 1. If you visit the URL that Heroku gave you, you will likely see an error:

     ![](/assets/migrations pending.png)
   
     The first thing to notice is that error messages look different in production mode. They don't give you the gory details of what went wrong, which makes sense because our users shouldn't see all that.
     
     So then how do we know what went wrong so that we can fix it? We'll see some more advanced tools later, but your first and foremost debugging tool is always **the server log**. In order to see the log of what's happening on our Heroku server, run the command:
     
     ```
     heroku logs --tail
     ```
     
     This command will show us what's going over there in California:
     
     ![](/assets/heroku log.png)
     
     You'll notice that the production server log is not as helpful as the development log! What I do is clear the Terminal with <kbd>Cmd</kbd>+<kbd>K</kbd>, and then refresh the request that was causing the error. I then scroll to the top of the mess, and start to look through carefully for the error message.
     
     You will eventually see something like this:
     
     ```
     ActiveRecord::StatementInvalid (PG::UndefinedTable: ERROR:  relation "users" does not exist
     ```
     
     `PG::UndefinedTable`... the issue is that, just like when we clone a new codebase to our own machine, we have to `rails db:migrate` to create[^7] the database! Right now, on Heroku, none of our migrations have been run.
     
     <kbd>Ctrl</kbd>+<kbd>C</kbd> to quit the Heroku server log and return to a Terminal prompt. To run commands on Heroku (rather than locally), we prefix them with `heroku run`:
     
     ```
     heroku run rails db:migrate
     ```
     
     Now if you visit your URL again, you'll see your live app!
     
     (**Note**: When you try `heroku run rails db:migrate`, there are a couple of common issues at this point:
     
      - If you see the error message "Directly inheriting from ActiveRecord::Migration is not supported. Please specify the Rails release the migration was written for":
      
          
    
    
     
     
     
     
     
      - "Index name 'index_active_admin_comments_on_author_type_and_author_id' on table 'active_admin_comments' already exists": See this note[^9]

    
    

[^1]: Heroku gives us a very powerful open-source database called Postgres. By default, a brand new Rails application uses a lightweight database called SQLite since it is already installed on basically every device that exists. We have to ensure that we make our app compatible with Postgres. Fortunately, since ActiveRecord handles translating our Ruby into SQL for us anyway, this requires no change to our application code. We simply need to switch to a different adapter when Heroku starts up the `rails server` in production mode (as opposed to development mode, which is what we do on our own machine).

[^2]: Any gems that are listed within the `:production` group will only be used when the `rails server` is started up in production mode. Usually, we start our server in the default mode, which is `development`. If you really wanted to, you could also restrict other gems to the `:development` group if they aren't used while serving actual requests; for example, `starter_generators`. This will result in a (small) performance boost.

[^3]: If the name you chose is taken, don't worry about it. Just choose something else that is unique. Ultimately you will hide these identifiers behind your own custom domain name anyway.

[^4]: Our first remote is named `origin`, by default. This is the remote that rules all the others: the one that we push our code to in order to collaborate with our team and hammer out the final version of the codebase. Nowadays, almost every team uses GitHub for this.

[^5]: Technically, it's one of Amazon's AWS servers, which Heroku rents and manages on our behalf.

[^6]: This idea of deploying an app via a simple `git push` was incredibly revolutionary. Heroku autodetects that it's a Rails codebase and does a _ton_ of work on our behalf to deploy it to an Amazon AWS server in production mode. Magical!

[^7]: You might be wondering why the database doesn't go to Heroku and GitHub along with all of the other code when we `git push`. There are lots of reasons, but for one, it would be a terrible idea to be using the same database while we're messing around developing as the one that our actual users are storing their precious data on. Size and data security are other reasons.

