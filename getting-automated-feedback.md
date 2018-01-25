![](/assets/Screen_Shot_2018-01-25_at_1_11_56_PM.png)![](/assets/Screen_Shot_2018-01-25_at_1_13_11_PM.png)![](/assets/Screen_Shot_2018-01-25_at_2_15_16_PM.png)# Getting automated feedback

## Set up a Github account

If you haven't created a Github account already, follow the steps in the [Setting up your Cloud9 workspace](setting-up-your-cloud9-workspace.md) guide to join Github and create a Github organization.

## Login to Canvas

Open up the Assignments tab and make sure they're sorted by type. 
![](/assets/login-canvas.png)

Scroll down to the assignment you want to start and click the link that says 'Load [your assignment name] in a new window'. 
![](/assets/load-assignment.png)

Authorize the FirstDraft Grades application to access your account. 
![](/assets/Screen_Shot_2018-01-25_at_1_15_14_PM.png)

Add your Github **organization name** and submit the form. 
![](/assets/Screen_Shot_2018-01-25_at_1_18_31_PM.png)

You should see something like the following page.
![](/assets/Screen Shot 2018-01-25 at 1.20.31 PM.png)

Open up your email account and look for for an email inviting you to the `appdev-projects` organization.

![](/assets/Screen_Shot_2018-01-25_at_1_22_47_PM.png)

Click the blue Join button to join the organization. 
![](/assets/Screen_Shot_2018-01-25_at_1_25_19_PM.png)

Then click the green Join button once you're redirected to Github.
![](/assets/Screen_Shot_2018-01-25_at_1_29_37_PM.png)

You should see feedback that you're now a member of appdev-projects. 

![](/assets/Screen Shot 2018-01-25 at 1.33.06 PM.png)

Now, you need to go back to your email account. You should see a new email that's inviting you to an appdev-projects team with the same name as your Github account. This makes it easy for us to separate your class projects from your personal projects. You don't need to take any action on this email, it's just a notification.  

Note: this is a different email than the one inviting you to the appdev-projects organization.
![](/assets/Screen_Shot_2018-01-25_at_1_36_57_PM.png)

Ok, now we can get the project loaded up in Cloud9 and try out the feedback feature. Load up your Cloud9 workspace. Run `cd ~/workspace` just in case you're not already in the base workspace folder. 

![](/assets/Screen Shot 2018-01-25 at 2.06.02 PM.png)

Then clone the assignment into Cloud9 using a command similar to `https://github.com/appdev-projects/project-repo-name` but make sure to replace `project-repo-name` with your specific project's repo name. You can find your repo name from the original instructions that popped up when you added the assignment from Canvas, or by going to https://github.com/appdev-projects/ and looking for the repo that matches your assignme![](/assets/Screen Shot 2018-01-25 at 1.13.11 PM.png)nt name. 
![](/assets/git-clone.png)

Then `cd` into your newly cloned project repo with something like `cd project-repo-name`, but again make sure to replace `project-repo-name` with your specific project repo's name.

![](/assets/cd-into-project-folder.png)

Run `bin setup` to get your project setup. 
![](/assets/bin-setup.png)

Run `rails grade:all`. You'll get asked for your access token, so just enter in the token you were given when you first loaded the Canvas assignment. If you lost the tab, you can always go back to the assignment in Canvas, reload it and find your token again. 

![](/assets/rails-grade.png)

You should see feedback that looks like![](/assets/rails-grade-feedback.png)

You can just click the Results URL to open up your feedback in a new tab. 
![](/assets/rails-grade-click-url.png)

![](/assets/rails-grade-results.png)

You can click on one of the tests to get more feedback on what might have gone wrong. 
![](/assets/rails-grade-results-details.png)
In this case, the test expected to find an element with a class of `word_count` that contains the number 10, but instead it only found the content "Replace this string with your answer". 

Whenever you've made changes, you can run `rails grade:all` in your Cloud9 terminal and you should see updated feedback. 
