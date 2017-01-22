# The Rails Console

The Rails Console is a quick, interactive way to test out Ruby expressions.

![](/assets/rails_console.gif)

When I am setting out on a new programming task, or when I have to debug something that isn't working the way I think it ought to be, I usually begin by playing around in the Console. I find the quick feedback that it provides useful; and once I've found the Ruby methods that do what I need, I then go write them down for good in a `.rb` file.

To launch a Console session,

 1. `cd` into the root folder of a Rails app. (I usually open a second command line window to do this, while leaving my `rails server` running in the first one.)
 1. Run the command `rails console`, or `rails c` for short. This will launch a new (text-only) app.
 1. You can then type any Ruby command you want at the slightly different looking prompt that appears (it will look something like `2.x.x :001 >`).
  - Sometimes you might get into a weird state with your commands (if, for example, you forget your closing `"` on a string or `]` on an array). To reset and get out of the weird state, press <kbd>Ctrl</kbd>+<kbd>C</kbd>. Then press the Up arrow to recover your last command, and fix the mistake.
 1. When you are done testing out Ruby one-liners, type `exit` and press <kbd>return</kbd> to shut down that program and return to the regular old command prompt.
 
That's it! After you've played around in this handy sandbox and discovered the Ruby you need to solve your problem, you are ready to head over to Atom and write it down permanently in a `.rb` file. Have fun!


