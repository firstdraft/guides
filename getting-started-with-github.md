# Getting Started With GitHub

## Pulling Code Down from GitHub.com

We're going to use GitHub for all of our code-sharing and submission.

### Vocab

All of our apps are just a folder with some files (maybe some HTML files, some CSS files, etc) and other folders in it. We call the top-level folder a **"repository"**. You'll find the list of the repositories we'll work on during this course on the organization page (your course org is probably called something like `appdevwinter2017`):

```
https://github.com/COURSE_ORGANIZATION
```
    
Each repository's original URL will look like this:

```
https://github.com/COURSE_ORGANIZATION/THE_PROJECT_NAME
```

When you **"fork"** one of the course repositories, all it means is "create a copy on your own GitHub.com account". Your copy will then live at a URL like this:

```
https://github.com/YOUR_USERNAME/THE_PROJECT_NAME
```

That way, you can upload (known as "pushing" or "syncing", in GitHub terminology) your changes to it. Syncing changes to your repo is how you will submit your work. If you try to sync changes to the original course copy, it will (correctly) tell you that you don't have permission to, so you have to remember to fork as your very first step of any project.

After you fork the repo, you'll **clone** your fork. **"Clone"** just means "download from GitHub.com to your own computer", but it's better than downloading the ZIP:

 1. Most importantly, cloning maintains a connection back to the mothership so you can sync your changes to the cloud.
 1. Also, it automatically creates a folder for you and unzips the contents there.

To make it easier to manage this process, we are going to use the official GitHub Desktop app.

### Install the GitHub Desktop App

First, [sign up](https://github.com/join) for a free GitHub account if you haven't already.

Then, download the GitHub app ([Mac][3] or [Windows][4]).

> NOTE: If you have a version of Mac OS X older than 10.9, you can either update to the latest release (recommended) or try these links: [OS X 10.8](https://web.archive.org/web/20141011004908/https://mac.github.com/), [OS X 10.7](https://web.archive.org/web/20140704072852/https://mac.github.com/)

<img src='http://ask.initialversion.com/uploads/default/44/616e77e081ec9508.png' width="645" height="500"> 

Install the app and open it up. When it asks, you'll have to provide your GitHub login and password.

<img src='http://ask.initialversion.com/uploads/default/45/e1cdbae12d21a5b0.png' width="606" height="500"> 

Later, it will ask for your full name and email address. This is for "signing" work that you do; whatever you write down here will be visible to the world. If you want to keep your real email address private, then use `<username>@users.noreply.github.com` instead. So, for me, I entered

 - `Raghu Betina`
 - `raghubetina@users.noreply.github.com`
 
since `raghubetina` is my GitHub username. 

If at some point it asks you to Install Command Line Tools, go ahead and click that button. If it asks you to scan for existing repositories, say no.

You should end up at a screen that looks something like this:

<img src='http://ask.initialversion.com/uploads/default/46/030a6d94a8d62d8a.png' width="606" height="500"> 

**Windows users**, now is your chance to specify where you want to store all of the code you are going to write in this class. **For reasons that will become clear once we get to Ruby on Rails, I suggest you use a folder called `C:\Sites` as your default download location.** To do so, create a folder called "Sites" at the very top of your hard drive in Windows Explorer. Then, click **Tools > Options**:

<img src='http://ask.initialversion.com/uploads/default/47/098ba4d5e16352ac.png' width="606" height="500">

Then specify the folder that you want the GitHub app to use by default when it downloads files (e.g., change it to `C:\Sites`):

<img src='http://ask.initialversion.com/uploads/default/48/00fa1a365201c4d1.png' width="606" height="500"> 

### "Fork" to create your own copy of a repository

Next, both Mac and Windows users, **restart your browser**. Then, head over to our class's organization on GitHub. Select a repository to work on (for example, `filebox_with_polish`).

First, in the top-right corner, click the "Fork" button, and agree to fork the repository to your own account.

<img src="http://ask.initialversion.com/uploads/default/39/c669095af38890bc.png" width="645" height="500"> 

It will take a moment to prepare your fork (this might even happen instantaneously, so you may not see the screen below):

<img src="http://ask.initialversion.com/uploads/default/40/28eeb31173bbfbc1.png" width="645" height="500"> 

You should end up at a URL that looks like

    https://github.com/YOUR_USERNAME/filebox_with_polish

**This is very important; if you don't fork successfully to your own account, I will not see your submission in the end.**

### "Clone" to download your copy to your computer

Next, on **your individual fork's page** *(not the course's original copy's page)*, click the "Open in Desktop" button. You can find the Open in Desktop button by first clicking the green "Clone or Download" button in the top-right corner.

> You will have to restart your browser after installing the GitHub Desktop App for the very first time, or this button will just take you back to the page to download it.

<img src="http://ask.initialversion.com/uploads/default/41/a8d2ecbaa45c6a4c.png" width="645" height="500"> 

This should bring up the GitHub Desktop app you downloaded earlier, and ask you where to save the code. The first time you do this, the browser may ask your permission to launch an external application -- say yes. **Mac users**, this is your chance to specify where you want to download the files to:

<img src='http://ask.initialversion.com/uploads/default/49/fc831b1345c28a21.png' width="645" height="500"> 

A repository is just a folder that contains files and other folders. When you clone it, a folder will be created on your computer named after the repository, and all of the files will be downloaded into it. When you select a location, you are just selecting a parent folder. A subfolder named after the repository will still be created every time. **So, you can pretty much always select the same location to download to, and new subfolders will be created automatically for each repository.** I use a folder in my home folder just called `code`.

You have now downloaded the homework assignment. In the GitHub desktop app, you should see something like this (the exact contents of the files will be different depending on which repository you downloaded):

**Mac**

<img src='http://ask.initialversion.com/uploads/default/50/25313deda98ebc7c.png' width="645" height="500">

**Windows**

<img src='http://ask.initialversion.com/uploads/default/51/d020b2827cccde98.png' width="606" height="500">

In Atom, open the whole entire `filebox_with_polish` folder that you just downloaded.

<img src='http://ask.initialversion.com/uploads/default/52/79da861b50dedbff.png' width="606" height="500">

<img src='http://ask.initialversion.com/uploads/default/53/e87d2c16221dce8a.png' width="606" height="500"> 

It should open up all the files, and put them in a tree in the left sidebar for easy navigation.

(Mac users, you can right-click on a repository name in the left sidebar of the GitHub Desktop App and select "Open in Atom" to do this quickly. Windows users, you can right-click on a folder in Explorer and do the same. You can also drag the folder from Finder or Explorer onto the Atom app icon.)

## Pushing Changes Back to GitHub.com

As you make changes to the files on your computer, you should sync them back up to your account on GitHub.com often. To do this, you "commit" them, which means you take a snapshot of the project's current state (across all of its files), and then "push" (upload) the commit back up to GitHub.com.

### Make some changes

Let's make a couple of changes. In this example, I add an `h1` tag and a `p` tag. Your changes will be different based on what homework you are working on.

<img src='http://ask.initialversion.com/uploads/default/54/e10f2ef50a11d1ca.png' width="653" height="500"> 

In the GitHub desktop app, with the repository you are working on selected, click the Changes tab (Mac) or click "show" next to "Uncommited Changes" (Windows).

Notice that Git highlights exactly which lines you've added (green) and removed (red) since the last snapshot.

### "Commit" to take a snapshot

Type in a summary to describe the changes you made **(summary is required, but description is optional)**, and then click the Commit button. 

**Mac**

<img src='http://ask.initialversion.com/uploads/default/55/35f21e14d57d7fda.png' width="690" height="454"> 

**Windows**

<img src='http://ask.initialversion.com/uploads/default/56/375e40bfcc4192cb.png' width="606" height="500"> 

### "Sync" to upload back to GitHub.com

Next, click the Sync Branch button to send your changes up to your account on GitHub.com.

**Mac**

<img src='http://ask.initialversion.com/uploads/default/57/d69f78f099e28551.png' width="690" height="454"> 

**Windows**

<img src='http://ask.initialversion.com/uploads/default/58/437201b160030d25.png' width="606" height="500">

### Verifying that you submitted correctly

To verify that your changes were successfully uploaded to your account on GitHub.com, go back to your fork's page and make sure it received the changes:

<img src='http://ask.initialversion.com/uploads/default/59/42ed9057b9acf6f5.png' width="645" height="500">

As we get more comfortable with Git, you'll see how this workflow will give us a powerful version control and collaboration system. But for now, just think of it like Dropbox where you have to manually prompt it to upload new versions of your files.

## FAQs

### Did my submission work?

We see exactly what you see on GitHub.com, so you can check whether you submitted correctly simply by visiting your own fork's page:

    https://github.com/YOUR_USERNAME/week_1_homework

When was the file(s) you worked on last modified? What was the commit message? You should see your own.

Or just browse the code on GitHub.com and make sure you see your latest changes.

### It isn't letting me sync.

You most likely clicked the "Clone in Desktop" button on my copy rather than on your own fork. Move, delete, or rename the folder you have; then clone your own fork:

    https://github.com/YOUR_USERNAME/week_1_homework

Then paste in your solutions and try Committing and Syncing again.

### I am clicking Sync but nothing is showing up on my fork on GitHub.com.

You most likely forgot to make a Commit. First make some changes; then the Desktop App will allow you to enter a message where it says "Summary", and then click "Commit to master"; then try Syncing again.

### Nothing happens when I click "Clone in Desktop" on the website.

 - Did you restart your browser after installing GitHub Desktop for the first time?
 - The first time you tried it, did you say "Yes" when the browser asked your permission to launch an external app? If not, it may have remembered that preference and you may have to dig around in your settings to undo that.
 
    An alternative is to click the "+" icon in the GitHub Desktop app, select the "Clone" tab, and then search for your "week_1_homework" fork. Then click "Clone Repository", and it will have the exact same effect as the button on the site.

  [1]: https://gist.github.com/raghubetina/af08992989160a910ef7
  [3]: https://mac.github.com/
  [4]: https://windows.github.com/