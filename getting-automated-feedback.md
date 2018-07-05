# Getting automated feedback

## Set up a GitHub account

If you haven't created a GitHub account already, follow the steps in the [Setting up your Cloud9 workspace](setting-up-your-cloud9-workspace.md) guide to join Github and create a GitHub organization.

**Remember the name of the organization you created** — you'll need it soon.

## Login to Canvas

Open up the Assignments tab and make sure they're sorted by type.

![](/assets/login-canvas.png)

Scroll down to the assignment you want to start and click the link that says 'Load [your assignment name] in a new window'.

![](/assets/load-assignment.png)

Authorize the firstdraft Grades application to access your account. **Make sure to click the 'Grant' button next to the organization that you created when setting up Cloud9.**

![](/assets/authorize-first-draft.png)

Select the name of your GitHub **organization** and submit the form.

![](/assets/add-github-org-name.png)

The next screen will ask you to accept an invitation to a GitHub team. You can click the link on that screen to accept, or you'll have an invitation in your email inbox as well.

Once you've joined, you should see feedback that you're now a member of appdev-projects:

![](/assets/github-joined-org-feedback.png)

Now head back to the assignment in Canvas and click "Load assignment in a new tab" again. You should see something like the following:

![](/assets/grade-setup-instructions.png)

Ok, now we can get the project loaded up in Cloud9 and try out the feedback feature. [Create a Cloud9 workspace as usual](getting-started-with-cloud9.md). Note that the repo was automatically forked for you; you don't need to fork manually anymore.

`bin/setup` as usual.

![](/assets/bin-setup.png)

Run Project and Preview the live application as usual, at this point. Start working on the project to do whatever the instructions tell you.

**When you're ready for feedback**, try a new command at a new Terminal prompt:

```
rails grade
```

You'll be asked for your access token; **copy-paste it carefully from the grades.firstdraft.com page that you loaded from Canvas**.

![](/assets/rails-grade.png)

You should see feedback that looks like:

![](/assets/rails-grade-feedback.png)

You can just click the Results URL to open up your feedback in a new tab. 

![](/assets/rails-grade-click-url.png)

![](/assets/rails-grade-results.png)

You can click on one of the tests to get more feedback on what might have gone wrong:

![](/assets/rails-grade-results-details.png)

In this case, the test expected to find an element with a class of `word_count` that contains the number 10, but instead it only found the content "Replace this string with your answer". 

You can click the "Examine Test" button to read the actual Ruby of the automated test; it's surprisingly readable. Ruby's testing libraries use method names that are supposed to make tests readable even for non-technical managers and clients. You can see specifically what flow is being tested and what inputs are being used and what the expected output is, and try to reproduce the issue in your own app manually using the same inputs.

You can run `rails grade` in your Cloud9 terminal as many times as you want, and you will get a new updated build report each time. It will only report your highest score back to Canvas, but be sure to make git commits often from `/git` so that you can experiment freely on new tasks without worry about breaking existing functionality.

### Remember that your first job is always to make your app work like the target. You should not rely exclusively on the automated tests; click through the target and your own app manually and get them to match behaviors first.
