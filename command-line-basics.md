# Command Line Basics

<iframe src="https://player.vimeo.com/video/141268631" width="640" height="400" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>


## See what folder you are currently in

### Mac

The "print working directory" command:

    pwd
    
### Windows

It should tell you in the prompt behind your cursor, e.g., `C:\Users\raghubetina\Desktop`

## See the contents of the folder you are currently in

### Mac

The confusingly named "list segments" command:

    ls
    
### Windows

The "dir" command:

    dir

### Navigate to a folder

The most important command to learn is the "change directory" command, `cd`. You always use `cd` along with the name of a folder you want to navigate to:

    cd code
    
A few things to keep in mind:

 - A folder with the name you give the `cd` command must exist in your *current working directory*. So you have to be aware of where you are, and what child folders are available, at any given time. Use the `ls`/`dir` commands for that.
 - There are a few special nicknames that you can give the `cd` command no matter where you are currently located:
  - `cd ..`: go back up to parent folder
  - Mac: `cd ~`, Windows: `cd \`: jumps to top-most folder
 - If a folder you want to navigate in to has spaces in its name, you must enclose the whole name in quotes: `cd "Program Files"`
 - You can also give the `cd` command the full path to the folder you want to go to. This is often helpful on Windows, because you can navigate to the folder using Windows Explorer and then copy the path from the address bar.

        cd "C:\Users\rbetina\code\webdev\week_3_homework"
        
 - On Windows, you can right-click the Command Prompt shortcut and under Properties, choose which folder it Starts In. Set this to [whatever default you chose for your GitHub Desktop app](https://gist.github.com/rbetina/22186869342fce3bec6b#install-the-github-desktop-app) to clone code to.
        
## A few notes on Command Line vs Rails Console

Remember, the Command Line is a completely different animal than `rails console`. Your command prompt looks something like

**Windows:**

    C:\Users\rbetina\code>

**Mac:**

    Raghus-MacBook-Pro:~ raghubetina$ 

Valid things to do at the command line include:

 - Navigating with `cd`, `ls`, etc
 - Launching the Rails Console app with `rails c`
 - Running Rails commands with `rails ...`

Once you have launched Rails Console, **you are in a different world**. None of the above commands are valid Ruby, so you will get errors if you try them. You should be able to tell whether you are in Rails Console or at the command line because the prompts look different. The console prompt looks something like `2.2.4 :001 >` or `pry(main)>`.

In this world, you are allowed to enter valid Ruby expressions like `"howdy world".capitalize` or `2 + 3 * 4`

**If you start entering some Ruby into console and mess up, and it gets stuck in a weird state, Ctrl-C to reset it.**

To get out of console and go back to the command line (for example, to run a Ruby source code file), use `exit`.

If you want, you can open two Terminal tabs or windows, and use one for console and the other for command line stuff.

### Learn More

[Unix for the Beginning Mage](http://unixmages.com/ufbm.pdf), Chapters 1 and 2 (or more if you are interested).