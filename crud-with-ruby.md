# CRUD with Ruby

Here is a quick reference on how to insert, retrieve, update, and delete rows from your database tables using our ActiveRecord-backed Ruby classes.

## Adding Tables to the Database

First, we need a Ruby class to represent the real-world thing we're trying to model, and we need an underlying database table to store information about each individual thing.

Rails includes an easy generator to help us get set up with both of these things quickly. Supposed I wanted to create a table to store instructors, with two string columns `first_name` and `last_name`. I could use this shortcut from the Command Line:

    rails generate model instructor first_name:string last_name:string

Notes: `g` is short for `generate` , the same way `s` is short for `server` and `c` is short for `console`. Also, be sure that the name of your model (the thing that goes after `rails g model`) is **singular**.

Commonly used datatypes for columns:

    :boolean
    :date
    :datetime
    :decimal
    :integer
    :string
    :text
    :time

If you execute this command, you'll see that Rails has written two files for you. We could write these files by hand, but since they are pretty formulaic, the shortcut can do the work for us:

 - It creates a Ruby class for us in `app/models` named `Instructor`, and made it inherit database-related superpowers from `ActiveRecord::Base`.
 - It creates a migration for us in `db/migrate`, and added instructions to it to create a table called `instructors`, with the columns/datatypes that we specified after the model's name.

Go open up the migration file in Atom and make sure it looks good. You have this one chance to correct any errors or omissions; once you execute it, this file will never be run again.

If it looks good, use the

    rake db:migrate

command to actually execute the code in the migration file and create your table. Now you are ready to start creating rows in the table.

> ### Aside: Making Changes To Your Database

> We have a few tools to make changes to our database once we have already run our migrations.

> First and foremost, we can generate new migrations to add new tables and modify existing tables. To modify existing tables, the most common tools we use are `add_column` and `remove_column`.

> Simply generate a new **migration** (not a whole **model** like above) like

>     rails g migration AddTitleToInstructors

> or

>     rails g migration RemoveLastNameFromInstructors

> Then, go into the new migration file and add instructions to make the change you want within the `change` method (or the `up` method, if that's what you find inside instead of `change`):

>     def change
>       add_column :instructors, :title, :string
>       remove_column :instructors, :last_name
>     end

> Then execute the instructions with `rake db:migrate`.

> If your database gets into a weird state (usually caused by deleting old migration files), your ultimate last resort is

>     rake db:drop

> This will destroy your entire database and all the data within it. Then, you can re-run all your migrations from scratch after fixing them to be however you like.

> Much more information about migrations can be found at the official Rails Guide:

> http://guides.rubyonrails.org/migrations.html

## CRUD with Ruby

Now that you have your model class defined and your database table set up, you can start saving data permanently. Fire up your `rails console` from within the root folder of your application.

#### Create 

    i = Instructor.new
    i.first_name = "Raghu"
    i.last_name = "Betina"
    i.save

Now you can just type `i` and it should show you that `i` has been inserted into the database and it has been assigned an ID number.

#### Read

To retrieve all of the rows from a table, you just ask the Class:

    a = Instructor.all

This will return to you an Array-like object, and you can do all the Array kinds of things with it; `.each`, `.count`, etc.

You can also scope it down a bit:

    f = Instructor.where({ :last_name => "Betina" })

This will return a collection of all rows which match the criteria (no matter how many matches there are, you will get back an array; it might be empty, or have only one element, or have a thousand elements).

To retrieve a single row, you need to know what you are looking for. Do you want the row with first name "Raghu"? Then do:

    i = Instructor.find_by({ :first_name => "Raghu" })

In general, the `YourModel.find_by()` method needs to know the `{ :column => "criteria" }` to lookup by.

Do you want the row with ID number 1? Then do:

    i = Instructor.find_by({ :id => 1 })

Or, since finding a row by ID is so common, and since every table has an ID column, we can use the shorthand:

    i = Instructor.find(1)

Once you have found a row, you can ask it for its attributes, i.e., its cell values under particular columns:

    i.first_name # => "Raghu"
    i.last_name # => "Betina"

#### Update

To update a row, first you need to find it:

    i = Instructor.find(1)

And then assign whatever new values you want to:

    i.first_name = "Raghuveera"

And then save.

    i.save

That's it.

#### Delete

To delete a row, first find it:

    i = Instructor.find(1)

And then,

    i.destroy

Pretty cold.

### Querying

For a simple lookup of a single record, we use the `.find_by` or `.find` methods as described above.

Our primary tool to query our tables for richer information than simple lookups is `.where`. **The `.where` method will always return an ActiveRecord Collection of results, whether there are zero matches, one match, or a thousand matches.** It's up to you, then, to pull each row out of the collection and do whatever you need to with it; exactly as you do after `.all`.

`.where` can be used to look stuff up just like `.find_by`, if we provide a list of columns and criteria that we want to match within a hash:

    Instructor.where({ :last_name => "Betina" })
    
You can be more specific and add multiple criteria to the hash (results will match all of them):

    Instructor.where({ :last_name => "Betina", :title => "Lecturer" })

`.where` can also be used to search for partial matches by passing a fragment of SQL in a string, rather than passing a hash:

    Instructor.where("last_name LIKE '%bet%'")
    
The `%` are wildcard characters, which match anything in that position.
    
You can search for rows less than or greater than certain criteria:

    Instructor.where("age > 30")
    Instructor.where("last_name >= 'A' AND last_name <= 'C'") 
    
That last query, for a value within a range, can be more easily written as

    Instructor.where(:last_name => ('A'..'C'))
    
This is particularly nice for searching for records within a particular range of times:

    start_date = 7.days.ago
    end_date = Date.today
    Instructor.where(:created_at => (start_date..end_date))
    
Remember, with Ruby Ranges, two dots means inclusive of the second value, and three dots means exclusive of the second value. E.g., `(1..4)` is 1, 2, 3, and 4; `(1...4)` is only 1, 2, and 3.

You can even use an Array in the argument to `.where`; it will then bring back the rows that match ANY of the criteria for that column:

    Instructor.where({ :last_name => ["Betina", "Venkataswamy"] })

Once you've retrieved the right subset of records, you can peel off the values in just one column with `.pluck`:

    Instructor.where(:created_at => (start_date..end_date)).pluck(:first_name)
      # => ["Raghu", "Arjun"]

Other useful query methods are [.order][1], [.limit and .offset][2], and [calculations like .minimum, .maximum, and .average][3].

Much more information about querying can be found at the official Rails Guide:

http://guides.rubyonrails.org/active_record_querying.html


  [1]: http://guides.rubyonrails.org/active_record_querying.html#ordering
  [2]: http://guides.rubyonrails.org/active_record_querying.html#limit-and-offset
  [3]: http://guides.rubyonrails.org/active_record_querying.html#calculations