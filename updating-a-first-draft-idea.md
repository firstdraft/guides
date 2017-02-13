# Updating a First Draft Idea



First Draft tries to demonstrate the same procedure that real-world dev teams use to propose and deploy changes to a codebase. Here is a very brief overview of some topics that we'll spend the rest of the quarter digging in to:



Suppose you design and publish the following app, which keeps track of movies:



![](https://d1b10bmlvqabco.cloudfront.net/attach/ixm26m993e2ip/iexbf06baz6/ixqh2udg50l0/Screen_Shot_20170109_at_1.17.28_PM.png)



A few minutes later, once the idea has published, you refresh the page and discover two new links at the bottom: "GitHub" and "Launch":



![](https://d1b10bmlvqabco.cloudfront.net/attach/ixm26m993e2ip/iexbf06baz6/ixqh5j3vs5an/Screen_Shot_20170109_at_1.21.26_PM.png)

Clicking "Launch" will take you to the live version of the app, which you can play around with and attempt to CRUD data to verify that your domain model supports your user stories.



Suppose you realize that you forgot to include users and the ability to create a personal watch list by bookmarking particular movies. You revise your domain model, adding tables for users \(checking the box to indicate that they represent accounts\) and bookmarks \(to join them to movies\), and then publish again:



![](https://d1b10bmlvqabco.cloudfront.net/attach/ixm26m993e2ip/iexbf06baz6/ixqhb0vsvt7y/Screen_Shot_20170109_at_1.24.38_PM.png)



However, even after it's done publishing, the changes will not be reflected in the live version of the app. Here's why:



The first time you click "Publish", First Draft does three things on your behalf:



1. It writes a whole app for you based on your domain model.
2. It puts the code in a new project \(or
   **repository**
   \) on your GitHub account for you.
3. It also deploys the code to your Heroku account for you. Heroku is the hosting service we will use to host all of our apps, which is why when you click "Launch" you end up at a ".herokuapp.com" URL.



GitHub is a service that nowadays has become the center of the software development universe. You can think of it as Dropbox for developers -- a place to safely store code -- but with infinitely more powerful collaboration features. Click on the "GitHub" link and take a quick look. We'll spend a lot of time during this course becoming familiar with GitHub, but for now just note the name of the repository -- we'll need it in a moment. In this case, it is "must\_see\_movies".



The second time you click "Publish", after making edits, First Draft does the following:



1. It makes the changes based on your new, revised domain model.
2. As a real developer would, it puts the new code in a new 
   **branch**
   of the existing repository. A branch is essentially an alternate version of your codebase, and you can flip back and forth between branches trivially. This makes it very easy for different developers \(or even just yourself\) to work in parallel on different features without messing each other up.
3. It creates what is called a
   **pull request**
   on GitHub. This is what you would do when, as a member of a team, you have worked for a while on your assigned task and you are ready for feedback from the rest of your team. You
   _request_
   that your team review your changes, and, once approved, that they be
   _pulled_
   into the main branch.
4. _It does not deploy to Heroku yet,_
   since the changes need review.



Now, since we haven't learned how to code yet, reviewing the changes won't be very useful. But one day it will be very instructive. For now, we are just going to pull the changes in without review -- but first, we need to tell Heroku to automatically deploy any changes that we pull into the master branch. So, head over to[heroku.com](https://dashboard.heroku.com/)and find the app in your dashboard. The app will have the same name as the first part of the URL you land on when you clicked "Launch" \(for now, likely the only app you have\).



Then, under the "Deploy" tab, in the "Deployment Method" section, click "Connect to GitHub". It will pop up a dialog asking you to authorize Heroku from GitHub; do so. Then, search for the app's repository name and connect it. Finally, click "Enable automatic deploys": 





![](https://d1b10bmlvqabco.cloudfront.net/attach/ixm26m993e2ip/iexbf06baz6/ixqlbyv8q0pc/herokudeploy.gif)









Finally, to actually pull in the new changes, go back to the GitHub repository and click on the Pull Requests tab. This is the beating heart of most software projects these days; where the ball is moved forward and knowledge is shared. You should see a link titled "2nd draft"; click it. Then click the green "Merge" button at the bottom and confirm:





![](https://d1b10bmlvqabco.cloudfront.net/attach/ixm26m993e2ip/iexbf06baz6/ixqlyuw4mf0b/merge.gif)







If all goes well, after a few minutes, you should now see your new changes reflected in the live application \(it's asking me to sign in -- there are user accounts now!\):



![](https://d1b10bmlvqabco.cloudfront.net/attach/ixm26m993e2ip/iexbf06baz6/ixqm1npck2cl/Screen_Shot_20170109_at_3.38.06_PM.png)

Henceforth, whenever you Merge a Pull Request, the changes will be automatically deployed.



First Draft is a brand new system, so you might very well run into some bugs in the process. If you do, please let us know here and we'll help you resolve. Have fun!

