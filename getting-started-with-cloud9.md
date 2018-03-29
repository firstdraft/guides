# Starting on a project in Cloud9

## Make sure you've connected your GitHub account to Cloud9

Click the gear icon in the top-right corner of your Cloud9 dashboard and then select "Connected Services" in the left sidebar.

If it's not already connected, go check out [this section of the Cloud9 setup guide](setting-up-your-cloud9-workspace.md#connect-your-github-account-to-cloud9).

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