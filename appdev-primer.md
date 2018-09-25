# AppDev Primer

## IMDb

 - Check out the [real IMDb](https://www.imdb.com/chart/top).
 - Click around [Must See Movies](https://msm-associations-target.herokuapp.com/), a version of IMDb that we'll build during this course.
 - If you had to design 2D tables to store all of the information required by Must See Movies, what would they look like?
 - Find the handout in your packet which is the printed-out Must See Movies Database. Try to answer the questions based on the data in the tables. (You are playing the part of the _application logic_ layer.)
 - If we wanted to add the ability for users to sign up and bookmark movies that they intend to watch, like a to-do list of movies to see, how would you change your database structure?
 
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

Find the handout in your packet which is the printed-out Photogram Database. Try to answer the questions based on the data in the tables.

As you're answering them, think about: what's your process? If you had to explain the process for answering each question [to a five year old](https://vimeo.com/27060669) such that they could take over in the future, how would you do it?

## Entity Relationship Diagrams

A useful notation for database designs is [Entity Relation Diagrams](https://www.lucidchart.com/pages/er-diagrams). Let's try sketching out the database designs we came up with above.

## firstdraft Ideas

 - Sign up for a free [GitHub](https://github.com) account. If you're a student, you can sign up for the [Education Pack](https://education.github.com/pack) for various discounted services, although you won't need any for this course.
 
 - [Sign up for a free Heroku account](https://signup.heroku.com/) (if it asks for your preferred programming language, say Ruby)
 
 - Don't forget to verify your email address for both.
 
 - Use those two accounts to sign up at [https://ideas.firstdraft.com/](https://ideas.firstdraft.com/)
 
### Initial Setup

 - Click on the green plus icon at the homepage to create a new Idea.
 - Give it a name (required) and tagline (optional).
 - To add a table, drag the “New Table” button and drop it somewhere on the canvas.
 - Give the table a name in the dialog that pops up.
	- If each record in the table represents user accounts, check the "User Accounts?" box.
 - New tables automatically get `id`, `created_at`, and `updated_at` columns which will be automatically managed by the database.
 - To add your own columns to a table, click the green plus in its header.
 - Give each column a name and select a datatype for it:
	- Integer
	- String (text up to 255 characters)
	- Decimal
	- Time
	- Date
	- Datetime
	- Text (text of any length)
	- Boolean (true or false)
	- Image Upload (are you planning to allow users to upload an image with this column?)
	- Mappable Address (will this column contain an address that you will want to map?)

### Associating tables

#### Foreign keys

To associate tables, first and foremost we have to add our foreign key columns.

 - Wherever you've identified a one-to-many relationship, add a foreign key column to the appropriate side; **make sure you select `Integer` as the datatype**.
 - Wherever you've identified a many-to-many relationship, add a join model (if you haven't already) and add the necessary foreign keys for each side.
 
#### Drawing relationships

##### One-to-many

For each one-to-many, drag the primary key that you are planning to store and drop it onto the foreign key column that you've set up to store it.

 - Click anywhere in the primary key column first (e.g. Director's `id`), and then drop it on the foreign key column (e.g. Movie's `director_id`).
 - You can usually accept the defaults in the dialog that appears, but it might be educational to read it and try to make sense of it.

One-to-manies are **direct relationships** because the connection is made by directly storing the foreign key in one of the concerned tables.

##### Many-to-many

Many-to-manies are **indirect relationships** because we have to walk through two one-to-manies (through the join model) to get to our ultimate destination. You can think of a many-to-many as the combination of the two one-to-manies.

For example, to get the cast of a Movie, we first want to go to its `roles`, and then for each role we want to go to its `actor`.

 - Click on the double-headed blue arrow in the header of either table (e.g. Movie).
 - Drag it and drop it anywhere on the target table (e.g. Actor).
 - In the dialog that appears, first select the first of the two associations that you want to combine (e.g. `roles`).
 - Next, select the second of the two associations that you want to combine (e.g. `actor`).
- The default name suggested for the relationship is usually pretty good (e.g. `actors`, but you can customize it if you want  (e.g. `cast`).
 - That’s it! You can build up any association this way, even using an indirect as one of the ingredients. For example, you could create an indirect association between Director and Actor by combining `movies` and `cast`.

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