# Fixing your organization permissions

Once upon a time, we all [created our own GitHub organizations](https://guides.firstdraft.com/setting-up-your-cloud9-workspace.html#create-github-organization) to keep our classwork separate from our personal projects.

Since then, whenever we gave permission to a third-party (like Cloud9 or grades.firstdraft.com) to access our GitHub accounts, we were supposed to remember to grant access to our organization too. **If you forgot to click "Grant" next to the organization that you created before you clicked "Authorize", you're going to run into problems.** Let's fix it.

Go to GitHub and sign in. In this example, I am signed in as the user `demolearner1`. Click on the user icon in the top-right and find "Settings":

![](/assets/github-settings.jpg)

Next, click on "Organizations" in the left sidebar:

![](/assets/github-orgs.jpg)

Find the organization that _you_ created. You likely picked a name like `[YOUR USERNAME]-appdev`:

![](/assets/org-list.jpg)

Next, go to the Settings of the organization:

![](/assets/find-org-settings.jpg)

In the left sidebar, find "Third-party access":

![](/assets/third-party-access.jpg)

If it says that access is Denied next to Cloud9 or Grades, then proceed.

 - If it says that you approved both, then you are good to go; you can stop reading.
 - If neither Cloud9 nor Grades appears in this list, click the "Remove restrictions" button instead and call it a day.

![](/assets/access-denied.jpg)

Click on whichever one you denied and Grant Access:

![](/assets/grant-access.jpg)

You should see a message confirming that access has been granted:

![](/assets/access-granted-flash.jpg)

Repeat for the other third-party app if necessary and then you're set!