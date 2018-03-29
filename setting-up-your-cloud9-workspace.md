# Setting up your Cloud9 workspace

## Join GitHub

If you haven't already, [sign up for a free GitHub account](https://github.com/join) \(or sign in to yours if you already have one\):

![](/assets/join-github.png)

In this example screenshot, I chose a username of `demolearner1` — remember yours. Also, don't forget to check your email and verify the address you entered.

For now, think of GitHub like Dropbox-for-programmers; it's where we're going to store all of our code.

## Create GitHub organization

To keep things organized, we're going to create a separate GitHub organization account for you to store your AppDev projects under \(to keep them separate from the personal projects that you'll hopefully be building soon!\).

Click the `+` on the right side of the navbar and select "New organization":

![](/assets/new-organization.png)

Choose any name for the organization; most students choose `[YOUR USERNAME]-appdev`. In this example screenshot, I chose `demolearner1-appdev`:

![](/assets/org-name.png)

You can "Skip" or "Finish" the rest of the screens:

![](/assets/finish-org.png)

## Join Cloud9

I have emailed everyone invitations to join the firstdraft team on Cloud9, which is the online tool we'll be using to write and run all of our code. In your inbox, you should see something like this:

![](/assets/cloud9-invite.png)

If you don't have an invitation, let me know.

Click on the link in the email and you should arrive at a welcome page. Click "Create new account":

![](/assets/cloud9-welcome.png)

Answer the next few questions:

![](/assets/cloud9-name.png)

![](/assets/cloud9-username.png)

![](/assets/cloud9-student.png)

![](/assets/cloud-captcha.png)

And you should arrive at a screen with a "Join Team" button. Click it:

![](/assets/cloud9-join-team.png)

You should wind up at your Cloud9 Dashboard. You now have everything you need to develop applications!

### Connect your GitHub account to Cloud9

Let's connect your Cloud9 account to your GitHub account to make it easy to download projects.

Click on the gear icon in the top-right:

![](/assets/cloud9-settings.png)

Then, click on "Connected Services" in the left sidebar, and then click "Connect" next to "GitHub":

![](/assets/cloud9-connected-services.png)

It will send you to GitHub.com to give your permission to Cloud9 to access things. **Be sure to click "Grant" next to the name of the organization that you created **[**in an earlier step**](#create-github-organization)**:**

![](/assets/cloud9-github-oauth-1.png)

_Then_ click "Authorize C9":

![](/assets/cloud9-github-oauth-2.png)

Your Cloud9 and GitHub accounts are now linked, and you'll end up back at Cloud9.

### Add your Cloud9 SSH key to GitHub

Finally, we're going to add an "SSH key" from Cloud9 to your GitHub account. This will save you from having to type your GitHub password over and over whenever you want to sync your code.

In Cloud9's Settings, click SSH Keys. Then highlight and copy the entire sequence of characters on the bottom:

![](/assets/cloud9-ssh-key.png)

Back in GitHub, click your icon in the top-right and then select Settings:

![](/assets/cloud9-github-settings.png)

Then click "SSH and GPG keys" in the left sidebar, and then click "New SSH key":

![](/assets/cloud9-github-new-ssh-key.png)

Paste in the key that you copied from your Cloud9 settings and click "Add SSH key":

![](/assets/cloud9-add-ssh-key.png)

You should end up at a screen like this:

![](/assets/cloud9-github-key-added.png)

Your Cloud9 and GitHub accounts are now fully connected!

## Create a new workspace

Before you can do any work in Cloud9, you need to set up a new workspace. From your [Cloud9 settings page](https://c9.io/account/settings), click the "+" link at the top right of the page. 

![](/assets/cloud9-new-workspace.png)


Choose any name for the workspace; most students choose `appdev-workspace`. Your team name should reflect the current quarter in which you're taking this class. 

![](/assets/cloud9-new-workspace-2.png)

We're going to have some sensitive information, such as email passwords and API credentials, in our code. In order to protect them, we need to switch our workspaces to be Private. Fortunately Cloud9 gives all users one private workspace for free.

**Important: Make sure to check the "Private" option to keep your workspace private and the "Ruby" option to set up the workspace for Rails **

![](/assets/cloud9-new-workspace-3.png)

Then click "Create workspace". The next step could take a while \(several minutes\); give it some time:

![](/assets/cloud9-cloning-workspace.png)

> If you get a message that it failed and to contact support, [Cloud9 settings page](https://c9.io/account/settings) and try creating a new workspace again. \(If it still gets stuck after 3 attempts, send an email to the support address given and cc me on it.\)

Ultimately, you'll end up in your Integrated Development Environment \(IDE\). There are three main parts to this environment: a file explorer on the left, an editor that takes up most of the visual space on the top right and a gray-blue terminal at the bottom right:

![](/assets/cloud9-workspace-up.png)


You'll be spending a lot of time in your IDE in the coming weeks. As you work, click on the little grey circles to learn tips about how to use Cloud9 more effectively.

## Add Autosave

From the top menu bar, click on `Cloud9 > Preferences`: 
![](/assets/cloud9-plugins-12.pn](/assets/cloud9-autosave.png)

Then click on the "EXPERIMENTAL" menu option in the editor and make sure the "Auto-Save Files" dropdown is set to "After Delay":
![](/assets/cloud9-autosave-2.png)

## Add formatting plugins

I've developed a set of plugins for the class that will make your programming experience much smoother than Cloud9's default setup. The steps below will show you how to install each plugin into your workspace. 

First, type the command `gem install rufo` into your terminal at the bottom of the screen and press enter. Don't worry about fully understanding this command yet, we'll talk about what this means during our course. 

![](/assets/cloud9-plugins.png)

You should see some feedback that `rufo` was successfully installed:
![](/assets/cloud9-plugins-2.png)


### Install gems

Install another gem called `htmlbeautifier`. Type the command `gem install htmlbeautifier` into the next line of terminal and press enter. You'll see some feedback that `htmlbeautifier` was successfully installed.

![](/assets/cloud9-plugins-3.png)

Create a folder to store the plugins. Type the command `mkdir ~/.c9/plugins` into terminal and hit enter. This command will create a directory called `plugins` that's nested inside a directory called `.c9`. 

> Note: You won't see any feedback during this step.

![](/assets/cloud9-plugins-4.png)

### Clone plugins

Clone the plugins from our Github repositories into your Cloud9 workspace. Type the following commands into terminal, one line at a time and hit enter. You should see feedback after each command. 

First, type in: 
`git clone https://github.com/firstdraft/rubysnippets.git ~/.c9/plugins/rubysnippets`
![](/assets/cloud9-plugins-5.png)

Then, type in: 
`git clone https://github.com/firstdraft/formathtmlerb.git ~/.c9/plugins/formathtmlerb`
![](/assets/cloud9-plugins-6.png)

And finally, type in: 
`git clone https://github.com/firstdraft/formatruby.git ~/.c9/plugins/formatruby`

![](/assets/cloud9-plugins-7.png)

### Edit your initialization script

From the top menu bar, click `Cloud9 > Open Your Init Script`. 

![](/assets/cloud9-plugins-8.png)

You should see a file open up in the editor:
![](/assets/cloud9-plugins-9.png)

You can edit this file to include our plugins in your workspace. Copy the following code into the bottom of the `init.js` file: 

```
![services.pluginManager.loadPackage([
"~/.c9/plugins/rubysnippets/package.json",
"~/.c9/plugins/formathtmlerb/package.json",
"~/.c9/plugins/formatruby/package.json",
]);
```
![](/assets/cloud9-plugins-10.png)

Then press `cmd + s` (or `ctrl + s` on Windows) to save the file. You'll be prompted to reload the page, which you can do by just refreshing your browser: 
![](/assets/cloud9-plugins-11.png)

**That's it! You're Cloud9 environment is now setup. You should be good to go. **
