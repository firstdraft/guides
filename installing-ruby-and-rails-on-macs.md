# Installing Ruby and Rails on Macs

Ruby is a wonderfully simple language, and Rails is an astonishingly powerful framework. Unfortunately, just installing them can sometimes be the trickiest part of learning to code!

In this guide I'll lay out the least error-prone method of installing that we've found. Hopefully you'll have no issues and it'll be smooth sailing.

In case you do run into an error, first try restarting your computer and then re-try the last step that you got stuck on. If that doesn't work, don't get discouraged! Post a question on the forum with as much detail as possible (error message, etc) and we'll try to fix it together.

Let's go!

## Getting the Command Line Tools

Open your Terminal app. You'll find it inside the Utilities folder in your Applications, but there's a better way: Spotlight.

You could click the magnifying glass in the top-right corner of your screen to use Spotlight, but developers try to use their mouse as little as possible. Instead, press <kbd>⌘</kbd>+<kbd>Space</kbd>; that should pop up the Spotlight search bar. Start typing "ter...". Terminal should appear in the results. Use your arrow keys to reach it and hit <kbd>return</kbd> to launch.

A window should pop up with a blinking cursor. Terminal is a text-only interface; you can't use your mouse at all here. Use the left and right arrows and <kbd>delete</kbd> to correct errors.

Copy and paste

```bash
xcode-select --install
```

into Terminal and hit <kbd>return</kbd>. You should get a popup that says you must install developer tools. Click the "Install" button on the far right.

## Installing Homebrew

Next, copy and paste

```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

into Terminal and hit <kbd>return</kbd>. It will download and install Homebrew, which is sort of like an app store for open-source software. If it asks you to type in your login password, go ahead and do it. **Type carefully -- it won't look like anything is happening when you type, but it is.**

## Installing the latest stable Ruby

Next, copy and paste

```bash
\curl -L https://get.rvm.io | bash -s stable --ruby
```

into Terminal and hit <kbd>return</kbd>. (The leading slash is not a typo, you must include it.)

This step might take a while; it will download and install the latest version of Ruby. (Your Mac actually comes with Ruby installed, but it's an older version than we want.)

At some point it might ask you for your password; type the password that you log in to your Mac with (if you don't have one, you may have to temporarily add one and then re-run this command). **When you type your password, it will look like nothing is happening, but rest assured -- it is.** Type carefully and hit return when done.

Once it is done and returns you to the blinking cursor, Quit Terminal and then restart it.

## Installing a slightly older Ruby

We're going to install a slightly older Ruby as well. This may seem weird but it is so that we're all (Mac, Windows, and Linux users) on the same page. Copy and paste

```bash
rvm install 2.4.3
```

into Terminal and hit <kbd>return</kbd>. Then, copy and paste

```bash
rvm use 2.4.3 --default
```

into Terminal and hit <kbd>return</kbd>.

## Installing Rails

Now that we have installed an updated version of the Ruby language, it's time to install Rails! Copy and paste

```bash
gem install rails --no-ri --no-rdoc
```

into Terminal and hit <kbd>return</kbd>. This will install Rails and all of its dependencies. It might take a few minutes, but that's it!

## Making sure everything worked

You should be all set now; to confirm, type

```bash
ruby -v
```

in Terminal and hit <kbd>return</kbd>. You should see something like `ruby 2.4.3pXX`.

Type

```bash
rails -v
```

and hit <kbd>return</kbd>. You should see something like `Rails 5.1.x`.

Congratulations, you're now ready to build industrial-grade applications! Have fun!