# Fixing your organization permissions

Once upon a time, we all [created our own GitHub organizations](https://guides.firstdraft.com/setting-up-your-cloud9-workspace.html#create-github-organization) to keep our classwork separate from our personal projects.

Since then, whenever we gave permission to a third-party (like Cloud9 or grades.firstdraft.com) to access our GitHub accounts, we were supposed to remember to grant access to our organization too. **If you forgot to click "Grant" next to the organization that you created before you clicked "Authorize", you're going to run into problems.** Let's fix it.

Go to GitHub and sign in. In this example, I am signed in as the user `demolearner1`. Click on the user icon in the top-right and find "Settings":

![](/assets/github-settings.jpg)

Next, click on "Organizations" in the left sidebar:

![](/assets/github-orgs.jpg)

Find the organization that **_you_ created**. You likely picked a name like `[YOUR USERNAME]-appdev`:

![](/assets/org-list.jpg)

Next, go to the Settings of the organization:

![](/assets/find-org-settings.jpg)

In the left sidebar, find "Third-party access":

![](/assets/third-party-access.jpg)

 - If it says that you approved both, then you are good to go and you can go to the next section.
 - If neither Cloud9 nor Grades appears in this list, click the "Remove restrictions" button instead and you can go to the next section.
 - If it says that access is Denied next to Cloud9 or Grades, then proceed.

![](/assets/access-denied.jpg)

Click on whichever one you denied and Grant Access:

![](/assets/grant-access.jpg)

You should see a message confirming that access has been granted:

![](/assets/access-granted-flash.jpg)

Repeat for the other third-party app if necessary.

## Make sure that you've accepted your team invitation

Visit [this page](https://github.com/appdev-projects) and make sure that you _don't_ have a banner across the top asking you to accept our team invitation. (This invitation was sent a while ago via email; if you've already accepted it, the banner won't appear.)

## Launch an assignment from within Canvas

Head back to Canvas and click on whichever assignment you want to work on again **(don't just refresh it if you already had it up)**. You might be asked to enter your organization name — be sure to enter _your_ organization name, the one you created; not `appdev-projects`.

## Resetting OAuth permissions to square one

If for some reason you need to make a single-sign-on provider (like GitHub, Twitter, or Facebook) "forget" that you ever authorized a third-party app, maybe because you don't use it anymore or maybe because you want to change the permissions that you gave it, you need to delete or revoke the "access token" that you previously issued to it.

In the case of GitHub, go to your personal settings:

![](/assets/github-personal-settings.jpg)

Find "Applications" in the left sidebar:

![](/assets/github-applications.jpg)

Click the "Authorized OAuth Apps" tab and then click "Revoke" next to whichever one you want to "forget":

![](/assets/github-revoke-oauth.jpg)

Then, return to the third-party app and "Sign in with..." again to start over from scratch. In our case, click on an assignment from within Canvas again to re-start the authorization process — and this time don't forget to grant access to the organization that **_you_ created**.