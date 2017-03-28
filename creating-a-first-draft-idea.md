# Creating a First Draft Idea

[ideas.firstdraft.com](https://ideas.firstdraft.com) is a tool designed to help you plan out your app idea from an information-storage perspective.

## Domain Modeling

Now that we've identified the features we want to include in our experiment, it's finally time to start thinking about how we're actually going to code it up.

The primary thing we need to do is **identify the tables and columns** we need in our database to keep track of all the information required to support the user stories. This is known as **domain modeling**. If we can get this part right, the rest of the code practically writes itself (trust me, you'll see).

My process for domain modeling is, once I have my list of actions and information on each screen, and my user stories in front of me -- try to identify the important **nouns** in the app. These usually become tables -- for example, events, recipes, tweets, users, messages, etc.

For each table, try to identify the columns we need. What are all the attributes about that thing that you need to track? For example, for events, you probably need held_on (date), title (string), description (text), location (string), etc.

Start diagramming out your domain model in [First Draft](https://ideas.firstdraft.com/).

#### Associations

The last and most crucial step in domain modeling is identifying relationships between each pair of tables.

A relationship can be one of two types: one-to-many, and many-to-many.

For example, in Instagram, a photo can be associated to many comments, but a comment can only be associated to one photo. This is a one (photo) to many (comments) association.

On the other hand, in IMDB, a movie can be associated to many actors, and an actor can also be associated to many movies. This is a many-to-many association.

The first step is, try to go through all of your tables and identify all one-to-many associations.

Once you feel good about your one-to-manies, try to identify all the important many-to-manies too.

For all one-to-manies, decide which table should get the foreign key column, and what it should be called.

For all many-to-manies, decide on a name for the join model.

Add your associations, and any required join models and foreign keys, to your [diagram in First Draft](https://ideas.firstdraft.com/).

**You should now have a complete listing of all your tables and columns, including those needed to support your associations.**

**Once you've taken a stab at writing down your domain model, it's time to book an appointment with one of us to review it.** The more progress you make on your own with domain modeling, the more productive our chat will be.

### Have fun!

P.S. The domain modeling tool is under active development. You can test out experimental code generation functionality by clicking "Publish". Come back in a few minutes and refresh, and you should see buttons that lead to some code on GitHub and a prototype on Heroku. The hope is that by clicking through the prototype and entering some data, you will catch flaws in your domain model and can then go back and update your diagram. Please feel free to send us any and all feedback.
