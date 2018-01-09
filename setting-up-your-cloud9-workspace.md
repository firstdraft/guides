# Setting up your Cloud9 workspace

## Join GitHub

If you haven't already, [sign up for a free GitHub account](https://github.com/join) (or sign in to yours if you already have one):

![](/assets/join-github.png)

In this example screenshot, I chose a username of `demolearner1` — remember yours. Also, don't forget to check your email and verify the address you entered.

For now, think of GitHub like Dropbox-for-programmers; it's where we're going to store all of our code.

## Create GitHub organization

To keep things organized, we're going to create a separate GitHub organization account for you to store your AppDev projects under (to keep them separate from the personal projects that you'll hopefully be building soon!).

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

It will send you to GitHub.com to give your permission to Cloud9 to access things. **Be sure to click "Grant" next to the name of the organization that you created [in an earlier step](#create-github-organization):**

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

## Clone template workspace

We've set up a computer for you to do your work on that is pre-configured with handy shortcuts and other things. Let's get you a copy of it.

[Visit this URL](https://c9.io/raghubetina/appdev_workspace) and then click the "Clone" button in the top-right:

![](/assets/cloud9-clone-workspace.png)

Choose any name for the workspace; most students choose `[YOUR USERNAME]-workspace`. In this example screenshot, I chose `demolearner1-workspace`:

![](/assets/cloud9-name-workspace.png)

Then click "Create workspace". The next step could take a while (several minutes); give it some time:

![](/assets/cloud9-cloning-workspace.png)

> If you get a message that it failed and to contact support, [go back to this page](https://c9.io/raghubetina/appdev_workspace) and try cloning again. (If it still gets stuck after 3 attempts, send an email to the support address given and cc me on it.)

Ultimately, you'll end up in your Integrated Development Environment (IDE):

![](/assets/cloud9-workspace-up.png)

You'll be spending a lot of time in your IDE in the coming weeks. As you work, click on the little grey circles to learn tips about how to use Cloud9 more effectively:

![](/assets/cloud9-tips.png)

Happy coding!
