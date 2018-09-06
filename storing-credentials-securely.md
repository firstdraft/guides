# Storing credentials securely

Many times we have API credentials or other sensitive information that we don't want to paste directly into our code, because then the information would be exposed on GitHub. Unsavory types like to scrape GitHub for sensitive information like API keys and run up huge bills for compromised users.

Instead, we'll store this information in **environment variables**, which means it lives on the computer somewhere separate from our code, and then our code will read the variables to access it.

In Rails, the way to access environment variables is via the `ENV` hash. The `ENV` hash is available to you everywhere — views, controllers, models, `rails console`, rake tasks, etc. The keys in the hash are the names of any environment variables that exist on the computer you're using, and the values are the contents of the variables.

For example, if there was an environment variable on your computer called `zebra` that had a value of `giraffe`, this is how you would access it from within Rails:

```ruby
ENV.fetch("zebra") # => "giraffe"
```

## Creating environment variables

But how do we create the environment variables and store our secrets in them?

### Cloud9

> If you realize you've made an error on any of the following steps, just type in `cd ~/workspace` and hit enter. That should get you back to the starting point.

1. Type in `cd ~` and hit enter. This command should take you to the home folder of your workspace.
1. Type in `touch .bash_profile` and hit enter. This command creates a hidden file called `.bash_profile` in your home folder.
1. Type in `ls -a` and hit enter. You'll see a list of all the files in your current directory, including hidden files (the ones whose names start with a `.`).
1. Mouse over the filename `.bash_profile` and click it. The file should open up in your editor.
1. Add whatever environment variables you want in this file like so:
    ```bash
    export ALGORITHMIA_KEY="replace_me_with_your_key"
    ```

    The name of the environment variable goes on the left side of the `=`, and the value on the right.
    
    Notes: don't put spaces around the `=`, and don't forget the `export` keyword at the beginning of the line.

1. Back in Terminal, type in `cd ~/workspace` to go back to your main folder, or just close that tab.

    > If you ever need to reopen your bash profile (for example to add additional environment variables), type `cd ~`, hit enter, then type `ls -a`, hit enter and click on the file to open it.

1. **Close all Terminal tabs.**
1. **If you have a Rails server running, stop it and re-start it.** 
1. The values that we `export` in the `.bash_profile` file become key-value pairs in the `ENV` hash. For example, to access this sensitive info, **in a NEW Terminal tab** (it won't work in old tabs) we can open a `rails console` and type in:

    ```ruby
    ENV.fetch("ALGORITHMIA_KEY")
    ```

    and we should see output of

    ```ruby
    => "replace_me_with_your_key"
    ```

You can use this pattern throughout your Rails app to store and use sensitive info but prevent it from showing on GitHub when you push your code up.

## dotenv

If you're not using Cloud9, there's a slightly better way than storing your secrets in your bash profile; the `dotenv-rails` gem.

 - If you don't already have it, add `gem "dotenv-rails"` to your `Gemfile`.
 - In your `.gitignore` file, make sure that there's a line somewhere with `/.env*`.
 - Make a git commit for the above two changes, if necessary.
 - Create a file in the root folder of the app called `.env`. Then add your secrets to it; for example,

    ```
    CLOUDINARY_CLOUD_NAME="paste your cloud name here"
    CLOUDINARY_API_KEY="paste your api key here"
    CLOUDINARY_API_SECRET="paste your api secret here"
    ```

    Since `/.env*` is included in the `.gitignore` file, this file doesn't exist as far as git is concerned; so it's safe to put your secrets in it.
    
 - Restart your Rails server and you should now be able to access these values from the `ENV` hash, e.g. `ENV.fetch("CLOUDINARY_CLOUD_NAME")`.
 - [Read more about dotenv here](https://github.com/bkeepers/dotenv).
