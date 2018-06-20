# AppDev Primer

## IMDb

 - Check out the [real IMDb](https://www.imdb.com/chart/top).
 - Click around [Must See Movies](https://msm-associations-target.herokuapp.com/), a version of IMDb that we'll build during this course.
 - If you had to design 2D tables to store all of the information required by Must See Movies, what would they look like?
 - If we wanted to add the ability for users to sign up and bookmark movies that they intend to watch, like a to-do list of movies to see, how would you change your database structure?
 
## Entity Relationship Diagrams

A useful notation for database designs is [Entity Relation Diagrams](https://www.lucidchart.com/pages/er-diagrams). Let's try sketching out the data model for Must See Movies in an ERD.
 
## Very Best

 - Click around [Very Best](https://very-best-demo-pr-3.herokuapp.com/), another app we'll build during this course. You can sign in with any of the following (all of their passwords are `password`):
    - `alice@example.com`
    - `bob@example.com`
    - `carol@example.com`
    - `eve@example.com`
    
    Or you can sign up for your own new account (it doesn't need to be a real email address).
 - It's aim is simple; it allows you to keep track of which restaurant in the city serves your favorite version of a particular dish. Your reigning champ for deep dish pizza, for example, could be Pequod's; but you're always on the lookout for a better one.
 - If you had to design 2D tables to store all of the information required by Very Best, what would they look like?
 - What are the primary _entities_, or nouns, in the app? These are good candidates for tables.
 - What are the relationships between the entities?
    - For each one-to-many, which side gets the primary key?
    - For each many-to-many, what's a good name for the join model?
 - Try sketching an ERD.
 - On paper with permanent marker, create the tables and columns that you planned out.
 - Then set aside the permanent marker and, with pencil, CRUD the data to support the following actions:
    - An admin adds "Pot Pie", "Gnocchi", and "Chana Masala" to the list of dishes.
    - A user signs up with username "alice" and email "alice@example.com".
    - A user signs up with username "bob" and email "bob@example.com".
    - A user adds the venues "Plein Air", "Daisies", and "Rangoli".
    - Alice bookmarks Plein Air for Pot Pie and Daises for Gnocchi.
    - Bob bookmarks Rangoli for Chana Masala.
    
 How did your database do? Was it able to support all of the features of Very Best? If not, how would you modify it?

## Photogram

 - Click around [Photogram](https://photogram-final-target.herokuapp.com/), another app we'll build during this course. You can sign in with any of the following (all of their passwords are `password`):
    - `alice@example.com`
    - `bob@example.com`
    - `carol@example.com`

    Or you can sign up for your own new account (it doesn't need to be a real email address).
 - This is a simple clone of Twitter, but with photos. It's a public social network where anyone can follow anyone (and they don't have to follow you back).
 - If you had to design 2D tables to store all of the information required by Photogram, what would they look like? (Assume, for now, that image uploads are just another column type, like caption is text.)
 - What are the primary _entities_, or nouns, the app? These are good candidates for tables.
 - What are the relationships between the entities?
    - For each one-to-many, which side gets the primary key? Note that you can't have two columns with the same name in the same table (but it's okay to have two columns with the same name as long as they are in different tables).
    - For each many-to-many, what's a good name for the join model?
 - Try sketching an ERD.
 - On paper with permanent marker, create the tables and columns that you planned out.
 - Then set aside the permanent marker and, with pencil, CRUD the data to support the following actions:
    - A user signs up with username "alice" and email "alice@example.com".
    - A user signs up with username "bob" and email "bob@example.com".
    - A user signs up with username "carol" and email "carol@example.com".
    - Alice uploads a photo with caption "horses".
    - Bob uploads a photo with caption "bridge".
    - Carol uploads a photo with caption "firebreather".
    - Alice follows Bob.
    - Bob follows Carol.
    - Carol follows Alice and Bob.
    - Alice likes firebreather and bridge.
    - Bob likes horses.
    - Carol, Alice, and Bob all comment on bridge.

How did your database do? Was it able to support all of the features of Photogram? If not, how would you modify it?

## Photogram Database

Given an existing database and data, pretend you're the _application logic_ for a Twitter-like social network:

  - It's asymmetrical — Person A can follow Person B without B following A in return.
  - It's public — Permission is not required to follow someone, and all statuses are visible to everyone.

Since you're pretending to be the _application logic_ layer, try answering these questions: [Photogram Database Exercise](https://docs.google.com/spreadsheets/d/104IDD206ubqloGZbjtSUAYwfOsFpiC6bQ3C11Re57M4/edit#gid=0).

As you're answering them, think about: what's your process? If you had to explain the process for answering each question [to a five year old](https://vimeo.com/27060669) such that they could take over in the future, how would you do it?

## firstdraft Ideas

 - [Sign up for a free GitHub account](https://github.com/join)
 
 - [Sign up for a free Heroku account](https://signup.heroku.com/) (if it asks for your preferred programming language, say Ruby)
 
 - Don't forget to verify your email address for both.
 
 - Use those two accounts to sign up at [https://ideas.firstdraft.com/](https://ideas.firstdraft.com/)
 
## Recreate ERDs

### Must See Movies ERD

Try creating an ERD of Must See Movies in firstdraft Ideas.
 
### Very Best ERD

Try creating an ERD of Very Best in firstdraft Ideas. If you click Publish in the Tutorial, does the prototype allow you perform the following [user stories](https://www.mountaingoatsoftware.com/agile/user-stories)?

#### As an admin, I should be able to...

 - Add dishes from the admin dashboard located at `/admin` (you can sign in to the admin dashboard initially with username `admin@example.com` and password `password`).
 
#### As a user, I should be able to...

 - See the bucket list of dishes.
 - See which venue I have bookmarked for each dish, or choose one if I haven't.
 - Add a new venue.
 - See what other people have bookmarked at a particular venue.
 
Can you perform all of the user stories above? **Your prototype is not going to _look_ the same as the target yet**, but can you capture the required information?
 
### Photogram ERD

Finally: Draw an ERD for Photogram. If you Publish it, you should have an ugly, but functionally identical, version of [the social network](http://photogram-final-target.herokuapp.com/) that we'll be ultimately building during this course. Try signing up and playing around with it a bit. Can you post photos? Can you like photos? Can the app show you which photos you've liked? Can you follow other users? **Can the application show you the photos that were posted by the people that you follow?**

The interface is horrible, but — you just built a social network! Not bad! That's pretty much the trickiest database design you'll ever have to deal with. Now we'll learn some front-end and you'll be able to improve the interface, and we'll learn some Ruby so you can build whatever functionality you can imagine. But now you've already got a feel for designing the foundation of any application — **it's _data_ (or _domain_) model**.