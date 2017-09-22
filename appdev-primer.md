# AppDev Primer
 
## firstdraft Ideas

 - [Sign up for a free GitHub account](https://github.com/join)
 
 - [Sign up for a free Heroku account](https://signup.heroku.com/) (if it asks for your preferred programming language, say Ruby)
 
 - Don't forget to verify your email address for both.
 
 - Use those two accounts to sign up at [https://ideas.firstdraft.com/](https://ideas.firstdraft.com/)
 
### IMDb ERD

#### Our first task:
 
Let's draw an Entity Relationship Diagram (ERD) together for [IMDb firstdraft Target](https://appdev-primer-imdb.herokuapp.com/).

Try clicking Publish!

#### Our second task:

If we wanted to add users and the ability for users to bookmark movies that they intend to watch, how would it change our domain model?

Make the requisite changes and Publish again.

### Photogram Database

Given an existing database and data, pretend you're the _application logic_ for a Twitter-like social network:

  - It's asymmetrical — Person A can follow Person B without B following A in return.
  - It's public — Permission is not required to follow someone, and all statuses are visible to everyone.

Since you're pretending to be the _application logic_ layer, try answering these questions: [Photogram Database Exercise](https://docs.google.com/spreadsheets/d/104IDD206ubqloGZbjtSUAYwfOsFpiC6bQ3C11Re57M4/edit#gid=0).

As you're answering them, think about: what's your process? If you had to explain the process for answering each question [to a five year old](https://vimeo.com/27060669) such that they could take over in the future, how would you do it?
 
### Very Best ERD

Now that you've had some practice navigating an existing database, it's time for you to design one yourself, given a set of features.
 
Explore this app: [Very Best Target](http://very-best-demo-pr-3.herokuapp.com/). It's aim is simple; it allows you to keep track of which restaurant in the city serves your favorite version of a particular dish. Your reigning champ for deep dish pizza, for example, could be [Pequod's](http://pequodspizza.com/); but you're always on the lookout for a better one.
 
You can sign in to Very Best with usernames `alice@example.com`, `bob@example.com`, `carol@example.com`, or `eve@example.com`. All of the passwords are "`password`". Click around and try to identify all of the features of the application.
 
See if you agree that these are the features of Very Best (phrased in a particular format known as **user stories**):
    
#### As a user, I should be able to...

##### On the Dishes page

 - See the bucket list of dishes
 - See which venue I have bookmarked for each dish, or choose one if I haven't
 - Filter dishes by cuisine
 - Search dishes by name
 - Click a link to add a venue if it doesn't already exist

##### On the Dish Details page

 - Bookmark a new venue for that dish
 - See the venues I've bookmarked for that dish in the past

##### On the new venue page

 - Add a new venue
   - Name
   - Address
   - Neighborhood (optional)

##### On the Venues page

 - See a list of all venues that I've bookmarked
 - Filter venues by neighborhood
 - Search venues by bookmarked dish

##### On the Venue Details page

 - See which dishes I've bookmarked at a venue
 - Add a new bookmarked dish to the venue
 - See what others have bookmarked at the venue.

##### Notes

 - Initially, dishes aren't specific to a user; we, the site admins, will set up same the bucket list of dishes that all users will fill out.
 - Initially, users will all use the same big list of venues. If and when the dropdown gets too big and unwieldy, we'll figure something else out.
  
#### Once you have a sense of it, your task:
 
 - Design what you think the database would have to look like in order to support the app.
 - Draw an ERD in firstdraft.
 - Click Publish and test out your prototype! Can you perform all of the user stories above? (Ignore the fact that it's ugly for now; can it capture/display the required information?)
 
### Photogram ERD

Finally: Draw an ERD for [Photogram firstdraft Target](https://appdev-primer-photogram.herokuapp.com/users/sign_up). This is an ugly, but functionally identically, version of [the social network](http://photogram-final-target.herokuapp.com/) that we'll be ultimately building during this course. Try signing up and playing around with it a bit. Can you post photos? Can you like photos? Can the app show you which photos you've liked? Can you follow other users? **Can the application show you the photos that were posted by the people that you follow?**

The interface is horrible and clunky, but it technically does allow you to do all of those things, I think. A social network is just about the trickiest database design you're going to ever have (self-referential many-to-manies, oh  my!), but you've already [navigated it no sweat in the clipboard exercise](#photogram-database).

Now we just have to draw the ERD of that same database. Give it a try in firstdraft. Think you got it? Click Publish and wait a few minutes and refresh. When "Launch" button appears, click it and play around with the prototype. If you missed something, edit the ERD and try again.

The interface is horrible, but — you just built a social network! Not bad! Now we'll learn some front-end and you'll be able to improve the interface, and we'll learn some Ruby so you can build whatever functionality you can imagine. But now you've already got a feel for designing the foundation of any application — **it's _data_ (or _domain_) model**.