# Continuous Integration

Find the assignment in Canvas:

![](/assets/ci-assignment.png)

Open it in a new tab:

![](/assets/ci-load-in-new-tab.png)

The very first time, you'll have to authorize firstdraft to manage your GitHub repositories (you may have to sign in to GitHub):

![](/assets/ci-authorize-grades.png)

The very first time, it will ask you for your CircleCI API Token:

![](/assets/ci-circle-api-token.png)

To get one, go to [CircleCI](https://circleci.com/) and sign up **with your GitHub account**. Then, go to "User Settings" in the left sidebar and find "Personal API Tokens". Generate one and then copy-paste it back into the form:

![](/assets/ci-get-circle-token.png)

![](/assets/ci-paste-circle-token.png)

You should finally end up at GitHub.com on your fork of the project:

![](/assets/ci-forked-repo.png)

Set up [a Cloud9 workspace as usual](getting-started-with-cloud-9.md) and Run Project:

![](/assets/ci-running-app.png)

Make your first change to the code to make some progress:

![](/assets/ci-make-a-change.png)

In the bottom-right corner, notice the button that says "Git"; click on it:

![](/assets/ci-git-button.png)

Git is an extremely versatile tool that developers use to collaborate; for now, we're going to adopt a fairly simple but powerful workflow. First, in the pane at the top, you can see the changes that you've made highlighted:

![](/assets/ci-git-status-master.png)

What we'll always want to start by doing when we begin on a new feature is **create a branch**. You can do that in the pane on the right just below the changes. Choose any name that you like (keep it fairly short):

![](/assets/ci-create-a-branch.png)

![](/assets/ci-git-status-on-branch.png)

Now that we're on a new branch for our experimental work, let's take a snapshot of the current state of the project after the changes that we've made so far by **making a commit**. You can do that in the pane on the left just below the changes. Enter a short title (required), and a longer description (optional):

![](/assets/ci-make-a-commit.png)

Now that you've taken a snapshot of your work, it's saved for posterity and no matter how terribly wrong things go from here, it will be easy to snap back to this state; so you can experiment freely on future tasks. Let's push this snapshot up to GitHub.com so it's saved in the cloud:

![](/assets/ci-push-to-github.png)

Then, "Open a pull request into master":

![](/assets/ci-open-a-pr.png)

**Pull Requests** have developed into the central atomic unit by which software development moves forward; we'll discuss many techniques for using them effectively to make your teams stronger in future classes. For now, click "Create pull request":

![](/assets/ci-create-pr.png)

That's it, for now! Over time, we'll talk about how this workflow pays tremendous dividends if everyone on the team adheres to it. For now, just remember to **create branches freely while experimenting with solving new problems**, because it's very easy to jump between them in case you want to start over; and **make lots of commits so that you never lose work**.