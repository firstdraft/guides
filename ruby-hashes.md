# Ruby Hashes

Suppose we have an array of instructors and students:

```ruby
instructors = ["Raghu", "Don", "Ben"]
students = ["Jocelyn", "Arthur", "Tom", "Lindsey"]
```

Suppose we want to combine them into a roster, and add last names and roles?  One way is an Array of Arrays:

```ruby
people_in_class = [
  ["Raghu", "Betina", "Instructor"],
  ["Don", "Eisenstein", "Instructor"],
  ["Ben", "Block", "Instructor"],
  ["Arjun", "Venkataswamy", "Instructor"],
  ["Jocelyn", "Williams", "Student"],
  ["Arthur", "Benson", "Student"],
  ["Tom", "Flannigan", "Student"],
  ["Lindsey", "Kallo", "Student"]
]

"The last name of the 3rd person is #{people_in_class.at(2).at(1)}"
```

This may suffice if the list of attributes is small, but as we add others, "Last Access to Github", "Attendance Record", "Class Participation", ... we have to remember which index holds which attribute --- our code will be hard to read, hard to maintain, and prone to errors.

## A brief interlude: Symbols

There is one datatype that we haven't discussed until now that will come in handy: `Symbol`s.

Symbols are like `String`s: a sequence of characters. However, Symbols follow the same rules as variable names:

 - Cannot contain spaces
 - Can only contain lowercase letters, underscores, and numbers
 - Cannot begin with a number
 
Otherwise, they are just like strings, and we can use them to hold text data:

```ruby
"hello" # I am a String
:hello  # I am a Symbol
```

Symbols are created by starting them off with a colon. You don't need a closing colon, since they cannot contain spaces; Ruby can figure out where they end.

So, that's that. Symbols are lightweight strings. Let's continue.

## Hashes to the rescue

Back to the problem of storing a list of attributes about a person effectively, without mixing them up. 
`Hash`es are like `Array`s, except each cell isn't automatically numbered -- we have to name it ourselves. So instead of representing a person with an Array like `["Raghu", "Betina", "Instructor"]`, we instead can use a Hash like this:

```ruby
person1 = { :first_name => "Raghu", :last_name => "Betina", :role => "Instructor" }
person2 = { :first_name => "Arthur", :last_name => "Benson", :role => "Student" }
```

 - We create a Hash with curly braces, `{ }`, rather than square brackets.
 - We still separate elements in the list with commas.
 - Unlike with Arrays, **we must supply a label for every element**. The label precedes the element, and is separated from it by an arrow looking thingy, `=>`, which we call a "hash rocket". When I read it out loud, I read it as "goes to".

To access a piece of data, we use the name (we call these "keys") of the cell rather than the position:

```ruby
person1.fetch(:last_name) # => "Betina"
```

> Another shortcut syntax for accessing elements in a Hash that you will commonly see is
>
> ```ruby
> person1[:last_name] # => "Betina"
> ```
>
> Note that even though we use curly braces to create hashes, this shortcut syntax uses square brackets to access them. I prefer `.fetch()`, however.)

No more having to remember which position number maps to which attribute!

The keys can be any class — String, Fixnum, whatever — but we almost always use Symbols as keys to our Hashes. (I like using symbols as the keys simply because since values are usually strings, syntax highlighting makes keys stand out from values.)

You can add a new key/value pair to an existing Hash with `.store()`:

```ruby
person1.store(:office_hours, "Wednesday 9:00am - 2:00pm")
person2.store(:attendance, 0.95)
```

The first argument to `.store()` is the key you want to store the data under, and the second argument is the data itself. If the key already exists, its value will be replaced.

Note, these hashes now have different keys!

> Another shortcut syntax for storing elements in a Hash that you will commonly see is
>
> ```ruby
> person2[:attendance] = 0.95
> ```
>
> Note that even though we use curly braces to create hashes, this shortcut syntax uses square brackets to access them. I prefer `.store()`, however.)

## The Bottomline

Arrays are very useful for storing a list of things that are all basically the same, and so it's nice for Ruby to automatically number them for you.

But when you are storing a list of things that are categorically different, and you'd rather label them yourself, then Hashes are a better choice. That's about it!