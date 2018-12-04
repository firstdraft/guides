# `draft_generators`

Include this line in your `Gemfile`, which you'll find in the root folder of your app:

```ruby
# Gemfile

gem "draft_generators", :git => "https://github.com/firstdraft/draft_generators"
```

Then,

```bash
bundle install
```

## Resources

To generate a complete, database-backed Golden Seven web resource:

```bash
rails generate draft:resource <MODEL_NAME_SINGULAR> <COLUMN_1_NAME>:<COLUMN_1_DATATYPE> <COLUMN_2_NAME>:<COLUMN_2_DATATYPE> # etc
```

For example,

```bash
rails generate draft:resource photo source:string caption:text
```

- The model name must be singular.
- Separate column names and datatypes with colons (NO SPACES).
- Separate name:type pairs with spaces (NO COMMAS).

In other words, the format of the command is exactly the same as when you were [generating only a model and table](crud-with-ruby.md#adding-tables-to-the-database), but `model` is replaced with `draft:resource`.

> Note: `rails g` is short for `rails generate`, like `s` for `server` and `c` for `console`.

Run the command `rails db:migrate` to execute the instructions that the generator wrote for us to create the new table.

> #### If you generated something mistaken:

> - **If you already `rails db:migrate`d, then first**

> `rails db:rollback`
> to undo just the most recent migration. If you didn't `rails db:migrate` after you generated the resource, then no need to do this step.

> - **Next**,

> rails destroy draft:resource photo

> will remove all the files that it previously added. You can then re-generate from scratch.

## Application Layout

To generate an application layout file that includes links to Bootstrap, Font Awesome, and some boilerplate markup for a nav bar and alert messages, run the command

rails g draft:layout <THEME>

`<THEME>` can either be blank, or the name of any [Bootswatch](http://bootswatch.com) (downcase), e.g., `cerulean`.

It will warn you that it is going to overwrite your existing `application.html.erb` -- say yes if you are sure that's okay. Copy out any important stuff if necessary, to be re-pasted back in.

## Making Changes

That's it! You now have a solid starting point to work from.

If you decide, however, to add a new column, then you'll have to go in and edit all of the relevant files by hand.

There's no magic to this generator; all it did was automate the tedium of building The Golden Seven boilerplate by hand. From here on out, it's up to you.
