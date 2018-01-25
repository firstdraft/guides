# Getting automated feedback

## Set up a GitHub account

If you haven't created a GitHub account already, follow the steps in the [Setting up your Cloud9 workspace](setting-up-your-cloud9-workspace.md) guide to join Github and create a GitHub organization.

## Login to Canvas

Open up the Assignments tab and make sure they're sorted by type. 
![](/assets/login-canvas.png)

Scroll down to the assignment you want to start and click the link that says 'Load [your assignment name] in a new window'. 
![](/assets/load-assignment.png)

Authorize the FirstDraft Grades application to access your account. If you haven't already granted access, make sure to click the 'Grant' button. 
![](/assets/authorize-first-draft.png)

Add your GitHub **organization name** and submit the form. 
![](/assets/add-github-org-name.png)

You should see something like the following page.
![](/assets/grade-setup-instructions.png)

Open up your email account and look for for an email inviting you to the `appdev-projects` organization.

![](/assets/email-org-invite.png)

Click the blue Join button to join the organization. 
![](/assets/email-join-org.png)

Then click the green Join button once you're redirected to GitHub.
![](/assets/github-join-org.png)

You should see feedback that you're now a member of appdev-projects. 

![](/assets/github-joined-org-feedback.png)

You might see an email notification that you've been added to an appdev-projects team with the same name as your GitHub account. This makes it easy for us to separate your class projects from your personal projects. You don't need to take any action on this email, it's just a notification. 

[](/assets/github-team-added-notification.png) 

Note: this is a different email than the one inviting you to the appdev-projects organization.

![](/assets/github-team-added-notification.png)

Ok, now we can get the project loaded up in Cloud9 and try out the feedback feature. Load up your Cloud9 workspace. Run `cd ~/workspace` just in case you're not already in the base workspace folder. 

![](/assets/cd-workspace.png)

Then clone the assignment into Cloud9 using a command similar to `https://github.com/appdev-projects/project-repo-name` but make sure to replace `project-repo-name` with your specific project's repo name. You can find your repo name from the original instructions that popped up when you added the assignment from Canvas. If you lost the tab, you can always go back to the assignment in Canvas, reload it and find your token again. 

Then `cd` into your newly cloned project repo with something like `cd project-repo-name`, but again make sure to replace `project-repo-name` with your specific project repo's name.

![](/assets/cd-into-project-folder.png)

Run `bin setup` to get your project setup. 
![](/assets/bin-setup.png)

Run `rails grade:all`. You'll get asked for your access token, so just enter in the token you were given when you first loaded the Canvas assignment. 

![](/assets/rails-grade.png)

You should see feedback that looks like![](/assets/rails-grade-feedback.png)

You can just click the Results URL to open up your feedback in a new tab. 
![](/assets/rails-grade-click-url.png)

![](/assets/rails-grade-results.png)

You can click on one of the tests to get more feedback on what might have gone wrong. 
![](/assets/rails-grade-results-details.png)

In this case, the test expected to find an element with a class of `word_count` that contains the number 10, but instead it only found the content "Replace this string with your answer". 

Whenever you've made changes, you can run `rails grade:all` in your Cloud9 terminal and you should see updated feedback. 
