# Getting automated feedback

## Set up a GitHub account

If you haven't created a GitHub account already, follow the steps in the [Setting up your Cloud9 workspace](setting-up-your-cloud9-workspace.md) guide to join Github and create a GitHub organization.

## Login to Canvas

Open up the Assignments tab and make sure they're sorted by type. 
![](/assets/login-canvas.png)

Scroll down to the assignment you want to start and click the link that says 'Load [your assignment name] in a new window'. 
![](/assets/load-assignment.png)

Authorize the firstdraft Grades application to access your account. **Make sure to click the 'Grant' button next to the organization that you created when setting up Cloud9.**

![](/assets/authorize-first-draft.png)

Add the name of your GitHub **organization** (not your username) and submit the form.

![](/assets/add-github-org-name.png)

You should see something like the following:

![](/assets/grade-setup-instructions.png)

Open up your email account and look for for an email inviting you to the `appdev-projects` organization:

![](/assets/email-org-invite.png)

Click the blue "Join" button to join the organization:

![](/assets/email-join-org.png)

Then click the green Join button once you're redirected to GitHub:

![](/assets/github-join-org.png)

You should see feedback that you're now a member of appdev-projects:

![](/assets/github-joined-org-feedback.png)

You might see an email notification that you've been added to an appdev-projects team with the same name as your GitHub account. This whole process makes it easy for us to separate your class projects from your personal projects. You don't need to take any action on this second email; it's just a notification. 

![](/assets/github-team-added-notification.png)

Ok, now we can get the project loaded up in Cloud9 and try out the feedback feature. Open up your Cloud9 workspace. Run `cd ~/workspace` just in case you're not already in the base workspace folder. 

![](/assets/cd-workspace.png)

Download the code for the project to your workspace as usual, and as per the project instructions given in the `grades.firstdraft.com` page above.

```
git clone ...
```

(If you lost the `grades.firstdraft.com` tab with project instructions, you can always go back to the assignment in Canvas, refresh it if necessary, and click on the link again.)

![](/assets/cd-into-project-folder.png)

Run `bin/setup` as usual.

![](/assets/bin-setup.png)

Now try a new command:

```
rails grade:all
```

You'll be asked for your access token; copy-paste it carefully from the Canvas assignment page.

![](/assets/rails-grade.png)

You should see feedback that looks like:

![](/assets/rails-grade-feedback.png)

You can just click the Results URL to open up your feedback in a new tab. 

![](/assets/rails-grade-click-url.png)

![](/assets/rails-grade-results.png)

You can click on one of the tests to get more feedback on what might have gone wrong.

![](/assets/rails-grade-results-details.png)

In this case, the test expected to find an element with a class of `word_count` that contains the number 10, but instead it only found the content "Replace this string with your answer". 

Whenever you've made changes, you can run `rails grade:all` in your Cloud9 terminal and you should see updated feedback. 
