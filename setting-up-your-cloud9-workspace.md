# Setting up your Cloud9 account

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

I have emailed everyone invitations to join our team on Cloud9, which is the online tool we'll be using to write and run all of our code. In your inbox, you should see something like this:

![](/assets/cloud9-invite.png)

If you don't have an invitation, let me know.

Click on the link in the email and you should arrive at a welcome page. Click "Create new account":

![](/assets/cloud9-welcome.png)

Answer the next few questions:

![](/assets/cloud9-name.png)

![](/assets/cloud9-username.png)

When it asks you to tell them about yourself, say that you are a student and that you'll be using Cloud9 for coursework:

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

## Run a setup script

I've developed a setup script for your Cloud9 workspace that will make your programming experience much smoother than Cloud9's default setup. 

First, download the script from our repository by copying and pasting the following command into terminal, then hitting enter:

```
curl --remote-name https://raw.githubusercontent.com/firstdraft/cloud9-setup/master/goodies
```
![](/assets/cloud9-setup-script.png)

This command downloads a setup script called `goodies` into your workspace. You should see it in the file explorer to the left. 

Next, run the `goodies` script by copying and pasting the following command into terminal, then hitting enter: 

```
sh goodies 2>&1 | tee ~/workspace/cloud9-setup.log
```

![](/assets/cloud9-setup-script-2.png)

## Edit your initialization script

Even though you've just installed some custom plugins into your workspace, you still need to make sure they get loaded every time you open up Cloud9.

From the top menu bar, click `Cloud9 > Open Your Init Script`. 

![](/assets/cloud9-plugins-8.png)

You should see a file open up in the editor:
![](/assets/cloud9-plugins-9.png)

You can edit this file to include our plugins in your workspace. Copy the following code into the bottom of the `init.js` file: 

```
services.pluginManager.loadPackage([
  "~/.c9/plugins/rubysnippets/package.json",
  "~/.c9/plugins/formathtmlerb/package.json",
  "~/.c9/plugins/formatruby/package.json",
]);
services.settings.set("project/ace/@tabSize", 2);
```
![](/assets/cloud9-plugins-10.png)

Then press `cmd + s` (or `ctrl + s` on Windows) to save the file. You'll be prompted to reload the page, which you can do by just refreshing your browser: 
![](/assets/cloud9-plugins-11.png)

**That's it! Your Cloud9 environment is now setup. You should be good to go. **
