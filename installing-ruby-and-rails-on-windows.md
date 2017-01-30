# Installing Ruby and Rails on Windows

Ruby is a wonderfully simple language, and Rails is an astonishingly powerful framework. Unfortunately, just installing them can sometimes be the trickiest part of learning to code!

In this guide I'll lay out the least error-prone method of installing that we've found. Hopefully you'll have no issues and it'll be smooth sailing.

In case you do run into an error, first try restarting your computer and then re-try the last step that you got stuck on. If that doesn't work, don't get discouraged! Post a question on the forum with as much detail as possible (error message, etc) and we'll try to fix it together.

Let's go!

## RailsInstaller

We're going to be using an all-in-one installer that sets us up with almost all of the software we'll need. It's called "RailsInstaller", and it's an open-source project kindly maintained by the folks at Engine Yard.

Navigate to [http://railsinstaller.org](http://railsinstaller.org), scroll down, and find the big green button that says "Windows Ruby 2.3". Click it to download the installer:

![](/assets/download_rails_installer.png)

Find the file that was downloaded and double-click it. Accept the terms and install:

![](/assets/terms_of_service.png)

For the next few dialogs, you can accept the defaults and click "OK":

![](/assets/install_location.png)

It will take a few minutes to install...

![](/assets/install_progress.png)

but at the end, it should launch a black window that looks like this:

![](/assets/cannot_find_path.png)

(From now on, whenever I say "bring up your terminal", this is what I mean -- launch Command Prompt with Ruby and Rails, which you'll find among your applications in your Start Menu.)

### "The system cannot find the path specified" bug in RailsInstaller

As of this writing, there is a bug in RailsInstaller that we have to fix manually.

To find out whether you suffer from this bug, in the Command Prompt with Ruby and Rails, type

```
rails -v
```

after the prompt `C:\Sites>` at the bottom of the window and press <kbd>return</kbd>. If it says something like `Rails 5.x.x`, then you're all set and you should skip to the next section. If it says `The system cannot find the path specified`, like this:

![](/assets/bad_rails_v.png)

then follow these steps:

 1. In Atom, from the **File** menu, **Open folder...**:
 
    ![](/assets/open_folder.png)
 
 1. Locate and open the folder `C:\RailsInstaller\Ruby2.3.0\bin`:
 
    ![](/assets/bin_folder.png)
 
    You should end up at a screen that looks like this:
    
    ![](/assets/drawer.png)
 
 1. From the **Find** menu, **Find in Project**:
 
    ![](/assets/find_in_project.png)
    
 1. In the "Find in Project" field that appears at the bottom of the screen, paste the following (**be careful not to select any trailing or leading spaces when you copy**):
 
        C:\Users\emachnic\GitRepos\railsinstaller-windows\stage\Ruby2.3.0\bin\

    ![](/assets/first_find.png)

 1. Click "Find". It should locate 32 matches across 16 files:
 
    ![](/assets/first_find_results.png)
 
 1. **Leave the "Replace in Project" field blank** and then click "Replace All".
 
    ![](/assets/first_replace_all_dialog.png)
    
    Confirm, and you should see:
    
    ![](/assets/first_replace_all_results.png)
 
 1. One more to go: in the "Find in project" field, paste the following (be careful not to select any trailing or leading spaces when you copy):

        C:/Users/emachnic/GitRepos/railsinstaller-windows/stage/Ruby2.3.0/bin/

 1. Click "Find". It should locate 16 matches across 16 files:
 
    ![](/assets/second_find.png)
 
 1. Leave the "Replace in project" field blank and then click "Replace All":
 
     ![](/assets/second_find_confirm.png)

 1. Confirm the replacement, and then quit Atom.
 1. Restart the Command Prompt with Ruby and Rails.
 1. Retry `rails -v` at the command prompt. It should now work and tell you something like `Rails 5.x.x`:
 
    ![](/assets/good_rails_v.png)

If you see that, then you're all set!

## SSL Certificate

In order to write apps that interact with other apps like Google Maps (for getting directions) or Twilio (for sending text messages) securely, we need to download a bundle of CA Root Certificates.

 1. Right-click on [this link](http://curl.haxx.se/ca/cacert.pem) and chose "Save link as...". Save the file, called `cacert.pem`, into `C:\RailsInstaller`:

    ![](/assets/download_cacert.png)

 1. Search for "system" in the Start menu. You should see a result from the Control Panel -- launch it:
 
    ![](/assets/search_for_system.png)
 
 1. Find "Advanced System Settings" and click it:
 
    ![](/assets/advanced_system_settings.png)

 1. Find "Environment Variables" and click it:
 
    ![](/assets/environment_variables.png)
 
 1. Under "System Variables" (*not* "User Variables for..."), click "New":
 
    ![](/assets/new_system_variable.png)
    
 1. For the variable name, enter `SSL_CERT_FILE` and then click "Browse File":
 
    ![](/assets/ssl_cert_browse_file.png)
    
 1. Locate the `C:\RailsInstaller\cacert.pem` file that you downloaded earlier and click "Open":
 
    ![](/assets/locate_cacert.png)
    
 1. To confirm that it worked, make sure that you see the new environment variable on the list:
 
     ![](/assets/confirm_environment_variable.png)
     
Quit and restart your Command Prompt with Ruby on Rails, if you have one open. That's it! 
 
## Node.js

Finally, we need to install Node.js to act as the JavaScript runtime for Rails 5. That should mean absolutely nothing to you right now :)

All you need to do is download and run the installer from the [Node.js website](https://nodejs.org/en/download/). Choose the LTS option:

![](/assets/download_node.png)

Find the file that was downloaded and double-click it. Accept the terms and install:

![](/assets/node_terms.png)

For all of the dialogs, you can accept the defaults and click Next. It will take a few minutes to install:

![](/assets/node_install_progress.png)

After the installation is complete, restart your Command Prompt with Ruby on Rails. That's it!

## The End

Congratulations, you're now ready to build industrial-grade applications! Have fun!