# Atom Configuration

We're going to be using the plain text editor Atom for all of our code-writing in this course. In this guide, I'll show you the tweaks that I use to make it as helpful as possible.

First, [download Atom](https://atom.io/) and install it.

## Settings

After you've installed Atom, launch it, and then

 - Mac: Atom menu > Preferences
 - Windows: File menu > Settings

Here are the settings that I like to use:

 - Core Settings (tab on left)
  - Uncheck “Exclude VCS Ignored Paths”

- Editor Settings (tab on left)
 - Set a font size if you like.
 - Check “Scroll Past End”
 - Check “Show Indent Guide”
 - Check “Soft Wrap”

## Packages

Next, find the "Packages" tab on the left. Packages are plugins that add extra functionality to Atom, and developers are releasing new ones all the time.

Atom comes with some packages included out of the box, which we need to tweak a little:

 - **MANDATORY:** Search for the package "autosave".

     After it comes up, click its "Settings" button. There is a checkbox there for "Enabled". This is different from the package itself (in the search results) being enabled. **Check the "Enabled" box inside of the package settings. We may not have done this last step together in class.**

     This package makes it so that whenever you switch from Atom to Chrome, all of your changes to any open files are automatically saved. This is a huge help when we start working on 2, 5, or even 10 files at once.

 - Search for the "git-diff" package and in its settings check "Show Icons".
 - Search for the "tree-view" package and in its settings check "Auto Reveal".

Furthermore, lets install some third party packages from the community. Click the "Install" tab on the left sidebar, and search and install:

 - `Sublime-Style-Column-Selection` by bigfive: This allows you to hold <kbd>Option</kbd> (or <kbd>Alt</kbd> on Windows) while dragging your mouse to highlight vertically. Useful for changing a bunch of things on lines above and below one another at once.
 - `less-than-slash` by mrhanlon: This autocloses the most recently opened HTML tag when you start typing `</...`.
 - `atom-wrap-in-tag` by sanusart: This allows you to highlight some content and type <kbd>Ctrl</kbd>-<kbd>Shift</kbd>-<kbd>W</kbd> to wrap it an HTML tag.
 - `auto-indent` by griiin: This life-changing package allows you to press <kbd>Cmd</kbd>-<kbd>Shift</kbd>-<kbd>I</kbd> (<kbd>Ctrl</kbd>-<kbd>Shift</kbd>-<kbd>I</kbd> on Windows) to fix indentation for the entire file you are working in, without having to select certain lines or dig around in the Edit menu.

## Themes

If you like, you can select a different theme. I use the built-in Atom Light in class. There are also lots of [community-provided themes](https://atom.io/themes/list?direction=desc&sort=downloads).



