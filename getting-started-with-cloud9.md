# Getting Started with Cloud 9

## Make sure you've connected your GitHub account to Cloud9

Click the gear icon in the top-right corner of your Cloud9 dashboard and then select "Connected Services" from the left. Click on "Connect" next to GitHub and authorize Cloud9. **Make sure that you Grant Access to _your_ organization** before clicking "Authorize".

## Creating a workspace

Then, to start on Very Best, unlike the usual workflow, click on the "Repositories" link in the left sidebar:

![](/assets/click_repositories.png)

All three team members will have copies of the repository; you should pick one for all three of you to work on. The "owner" should add the others to it as collaborators.

Then, for all three team members, the repository should appear on this list. Make sure that you are all working on the same one, even though you might have your own showing up there too.

![](/assets/search_and_clone.png)

Click "Clone to edit" and then enter any name for the workspace. Select Public, and **select "Ruby"**. Then click "Create workspace".

![](/assets/configure_workspace.png)

![](/assets/creating_workspace.png)

## Setting up the project

You'll end up in your IDE (integrated development environment), which is like having a text editor and a command line interface to a computer with Ruby and Rails pre-installed all within a single Chrome tab.

Then, run the command `bin/setup` in the Terminal at the bottom of the window to get the project ready to go.

## Starting the server

On Cloud9, the full command you need to start the server is

```
rails server -b $IP -p $PORT
```

However, that's annoying to type, so Cloud9 provides us with the green "Run Project" button near the top-right of the window.

Click it and you'll have a live application running on the internet. You'll see the URL of your application in the server log in a new Terminal tab at the bottom, and you can open it up in a new Chrome tab:

![](/assets/rails_server.gif)

## Editing code

Change some code, save, and refresh your app:

![](/assets/change_code.gif)

![](/assets/other_urls.gif)

One last step: turn on Autosave.

![](/assets/autosave.png)

Then refresh your browser to apply the change.

There are other settings you can customize here too, if you like, but **always remember to turn on autosave for every project**.

Cloud 9 actually has a lot of cool features that we don't get when we work on our own computers like real-time collaboration, so you should explore! Have fun!

![](/assets/cloud_9_workflow.png)
