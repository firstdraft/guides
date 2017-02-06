# `starter_generators`

Include this in `Gemfile`, which is a file located in the root folder of your app:

```ruby
# Gemfile

gem "starter_generators", :git => "https://github.com/raghubetina/starter_generators.git"
```

Then, 

```bash
bundle install
```

## Resources

To generate a complete, database-backed web resource:

```bash
rails generate starter:resource <MODEL_NAME_SINGULAR> <COLUMN_1_NAME>:<COLUMN_1_DATATYPE> <COLUMN_2_NAME>:<COLUMN_2_DATATYPE> # etc
```

For example,

```bash
rails generate starter:resource photo source:string caption:text
```

 - The model name must be singular. 
 - Separate column names and datatypes with colons (NO SPACES).
 - Separate name:type pairs with spaces (NO COMMAS).

Note: `rails g` is short for `rails generate`, like `s` for `server` and `c` for `console`.

`rails db:migrate` to run the migration that the generator wrote for us to create the new table.

> #### If you generated something mistaken:

>  - **If you already  `rails db:migrate`d, then first**

>         rails db:rollback
>     to undo just the most recent migration. If you didn't `rails db:migrate` after you generated the resource, then no need to do this step.

>  - **Next**,

>         rails destroy starter:resource photo

>     will remove all the files that it previously added. You can then re-generate from scratch.

## Application Layout

To generate an application layout file that includes links to Bootstrap, Font Awesome, and some boilerplate markup for a nav bar and alert messages, run the command

    rails g starter:style <THEME>

`<THEME>` can either be `default`, or the name of any [Bootswatch][1] (downcase), e.g., `cerulean`.

It will warn you that it is going to overwrite your existing `application.html.erb` -- say yes if you are sure that's okay. Copy out any important stuff if necessary, to be re-pasted back in.

Boom, your app is now pretty! You'll still have to modify e.g. the navbar, but it gives you a solid starting point.

  [1]: http://bootswatch.com