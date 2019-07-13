# Getting automated feedback

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

Ok, now we can get the project loaded up and try out the feedback feature. `bin/setup` as usual, if you haven't already:

![](/assets/bin-setup.png)

Start working on the project to do whatever the instructions tell you. **When you're ready for feedback**, try a new command at a new Terminal prompt:

```
rails grade
```

You'll be asked for your access token; **copy-paste it carefully from the grades.firstdraft.com page that you loaded from Canvas**.

![](/assets/rails-grade.png)

You should see output that looks like:

![](/assets/rails-grade-feedback.png)

Copy-paste the Results URL into a new tab, or click on it (but make sure it isn't truncated).

![](/assets/rails-grade-click-url.png)

![](/assets/rails-grade-results.png)

You can click on one of the tests to get more feedback on what might have gone wrong:

![](/assets/rails-grade-results-details.png)

In this case, the test expected to find an element with a class of `word_count` that contains the number 10, but instead it only found the content "Replace this string with your answer". 

You can click the "Examine Test" button to read the actual Ruby of the automated test; it's surprisingly readable. Ruby's testing libraries use method names that are supposed to make tests readable even for non-technical managers and clients. You can see specifically what flow is being tested and what inputs are being used and what the expected output is, and try to reproduce the issue in your own app manually using the same inputs.

You can run `rails grade` in your Terminal as many times as you want, and you will get a new updated build report each time. It will only report your highest score back to Canvas, but be sure to make git commits often from `/git` so that you can experiment freely on new tasks without worry about breaking existing functionality.

### Remember that your first job is always to make your app work as described and test it manually yourself. You should not rely exclusively on the automated tests; they are a terrible way to debug.
