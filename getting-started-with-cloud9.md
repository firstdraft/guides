# Starting on a project in Cloud9

## Ensure your GitHub account is connected to Cloud9

Click the gear icon in the top-right corner of your Cloud9 dashboard and then select "Connected Services" in the left sidebar.

If GitHub is not already connected, go check out [this section of the Cloud9 setup guide](setting-up-your-cloud9-workspace.md#connect-your-github-account-to-cloud9).

## Creating a workspace

Then, to start on a project, click on the "Repositories" link in the left sidebar:

![](/assets/click_repositories.png)

You will see a list of all of your GitHub repositories. If you don't see the project listed there, go click on the assignment in Canvas again; that ought to "fork" ("make a copy", in GitHub lingo) it to your own organization. Then refresh the list in Cloud9.

You could also navigate to any project directly on GitHub, e.g. [appdev-project/rps-html](https://github.com/appdev-projects/rps-html) and click the "Fork" button in the top-right corner; then choose whether you want to copy it to your personal account or organization.

![](/assets/search_and_clone.png)

Click "Clone to edit" and then enter any name for the workspace. In the example below I named the workspace `ruby_intro`, but you might name it `rps-html` or whatever makes sense for the project you are working on.

Select **Public**, and select **Ruby** (very important). Then click "Create workspace".

![](/assets/configure_workspace.png)

![](/assets/creating_workspace.png)

## Setting up the project

You'll end up in your IDE (integrated development environment), which is like having a text editor and a command line interface to a computer with Ruby and Rails all within a single Chrome tab.

To get the individual project's dependencies set up, find the Terminal at the bottom. At a `$` prompt (click the green + for a new tab if you need to), type

```bash
bin/setup
```

and press <kbd>return</kbd> to get the project ready to go. **This will take a few minutes.** It's installing a bunch of powerful, industrial-grade software, all for free!

## Starting the server

Once `bin/setup` completes and you are returned to a blinking cursor at the `$` prompt, the full command you would need to type to start your web app server is

```
rails server -b $IP -p $PORT
```

However, that's annoying to type, so Cloud9 provides us with the green "Run Project" button near the top-right of the window instead:

![](/assets/cloud9-run-project.png)

If you click it, a new Terminal tab will pop up, and once the server launches it will give you a URL of the live application. Sweet!

## Editing code

Change some code, save, and refresh your app:

![](/assets/change_code.gif)

![](/assets/other_urls.gif)

Yay! We're programming!

## DON'T FORGET to turn on Autosave

From the top menu bar, click on `Cloud9 > Preferences`:

![](/assets/cloud9-plugins-12.pn](/assets/cloud9-autosave.png)

Then click on the "EXPERIMENTAL" menu option in the editor and make sure the "Auto-Save Files" dropdown is set to "After Delay":

![](/assets/cloud9-autosave-2.png)

## Enable Rails Goodies

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

## Explore

Cloud 9 actually has a lot of cool features that we don't get when we work on our own computers like real-time collaboration, so you should explore:

![](/assets/cloud_9_workflow.png)

There are little glowing bubbles all around that you should click on for tips and dismiss them once and for all:

![](/assets/cloud9-tips.png)