# Rock Paper Scissors

We are going to build a simple game. Users are allowed to choose Rock, Paper, or Scissors by visiting one of the following addresses:

 - `https://rps-rcav-[YOUR CLOUD 9 USERNAME].c9users.io/rock`
 - `https://rps-rcav-[YOUR CLOUD 9 USERNAME].c9users.io/paper`
 - `https://rps-rcav-[YOUR CLOUD 9 USERNAME].c9users.io/scissors`

And we will tell them whether they won or lost.

#### [Here is the target you will ultimately build.](https://rps-rcav-target.herokuapp.com)

## Setup

Set up the RPS RCAV project as usual. Click "Run Project" once you've done so and navigate to the live app and you'll see the usual "Welcome Aboard" page. 

**This is currently a brand new Rails app.** I've done nothing at all to it — this is how Rails apps come out-of-the-box when you run the `rails new my_fancy_app` command at a Terminal prompt (you can try it now if you want, but it will create a whole subfolder with an entire app inside).

## Route → Controller → Action → View

Since this is currently a brand new Rails app, it has absolutely no routes, controllers, etc.

Add support for each of the three addresses, `/rock`, `/paper`, and `/scissors`, one at a time. For each one,

 1. Connect the [RCAV dots](https://guides.firstdraft.com/rcav-flowchart.html) and display "Hi!" to prove that you did so. Make up whatever names you want for the controller and action.
 1. Now step back into the action and write some logic to determine whether the player won or lost. Put the computer move and the outcome into output variables.
 1. In the view template, display the output variables. Format it a little with some markup and some copy.

## Stretch Goals

Once you have completed the above for all three addresses,

 1. On each page, add links to get to the other two pages (so that our users don't have to keep typing into the address bar).

 1. Use [BootstrapCDN](https://www.bootstrapcdn.com/) to connect Bootstrap or a Bootswatch.

    You will find the `<head>` of _all_ of our view templates in the file `app/views/layouts/application.html.erb`, which is a wrapper or "layout" that surrounds every view template that we send to our users.

    If you go examine the `application.html.erb` file that we got out-of-the-box when we generated the new application, you'll see that it includes all of the usual HTML boilerplate -- `<!DOCTYPE>`, `<html>`, etc.

    Notice the line that says `<%= yield %>.` That is where the contents of our view templates get plugged in before the entire response gets sent to our users' browsers.

    This is a great way to DRY (Don't Repeat Yourself) up repetitive markup like navbars, footers, links to stylesheets, etc. It's one of _many_ advantages to using a dynamic framework like Rails over writing static HTML.

 1. Use some [Bootstrap classes and components](http://getbootstrap.com/) in your view templates.

 1. You can also add any images that you like to the `public/` folder, and use them as the `src` for `<img>`s.

    For example, if you create a file called `public/rock_image.jpg`, you can use it like this:

    ```html
    <img src="/rock_image.jpg">
    ```

    Notice that the file just get served directly from the root of the domain if you place it directly in the `public/` folder. You can also create subfolders to keep things organized, if you like.

 1. That said, [Font Awesome](https://fontawesome.com/icons/) has icons for rock, paper, and scissors. Find them and use them.

 1. If you want to, you can also create another stylesheet for additional styles in the `public/` folder and `<link>` to that.

 1. Add a root URL such that visiting the bare domain leads to a landing page with some information about the game. (Hint: the first argument of the route will just be the plain slash, like so:

        get("/", { # etc ...