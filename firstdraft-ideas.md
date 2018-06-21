### ideas.firstdraft.com

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


 