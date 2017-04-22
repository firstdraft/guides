# Glossary of Terms

#### Argument

An input to a [method](#method):

```ruby
"well, hello!".gsub("ll", "✌️") # => "we✌️, he✌️o!"
```

In the example above, the strings `"ll"` and `"✌️"` are both arguments to the method `gsub`.

The syntax for giving a method its arguments is to put them within parentheses immediately following the method's name; and if there are multiple arguments, then they are separated by commas.

While Ruby is pretty flexible about whitespace most of the time, remember: **don't put a space between the method's name and the parentheses that contain its arguments!**

Ruby does allow you to, optionally, omit the parentheses; and some Rubyists do prefer that style. So when you are reading Ruby around the internet, you will encounter things like this:

```ruby
"well, hello!".gsub "ll", "✌️"
```

It's just a matter of taste which style you use, but definitely don't use both parentheses _and_ a space, like this

```ruby
"well, hello!".gsub ("ll", "✌️") # wrong!
```

Personally, I prefer using the parentheses around arguments to keep it clear what goes with what. Otherwise I get confused, especially when there's more than one method on the same line.


#### Array

One of the built-in Ruby [classes](#class). It is one of the two primary classes we use to represent **lists of things**. (The other one is [`Hash`](#hash).)

Ruby represents the list within square brackets, with each element separated by a comma:

```ruby
["doug", "alice", "carol", "bob"]
```

Each element of an `Array` can be any Ruby object — even another `Array`.

A blank instance of `Array` can be created like any Ruby object, by calling `.new` on the class:

```ruby
a = Array.new
```

or by using the square bracket shorthand:

```ruby
a = []
```

You can add elements to an array with the `.push()` method, which takes one argument; the object you want to add to the end of array:

```ruby
a.push("doug")
a.push("alice")
a.push("carol")
a.push("bob")
```

There is also a shorthand for adding elements to an array with the `<<` ("**shovel**") operator:

```ruby
a << "doug"
a << "alice"
a << "carol"
a << "bob"
```

You can also pre-populate the array _in one fell swoop_ when you create it:

```ruby
a = ["doug", "alice", "carol", "bob"]
```

You can then access elements in the array by position number with the `.at()` method:

```ruby
a.at(1) # => "alice"
```

Notice that position numbers begin at `0`, not `1` as you might expect.

There is also a square bracket shorthand for accessing elements:

```ruby
a[1] # => "alice"
```

[Read more about arrays here.](https://guides.firstdraft.com/fundamental-classes.html#arrays)

#### Block

Some methods, like `gsub()`, require additional _data_ to do their job:

```ruby
"well, hello!".gsub("ll", "✌️") # => "we✌️, he✌️o!"
```
 
[Arguments](#argument) are pieces of data that a method needs as input in order to do its job. In the above example, `gsub()` needs to know which substring to replace and what to replace it with.

Other methods, like `.each`, require additional **instructions** to do their job:

```ruby
our_numbers = [4, 10, 6]        # Create an array of numbers
squared_numbers = []            # Create an empty array

our_numbers.each do |num|       # For each element in numbers, (refer to it as "num")
  square = num * num            # Square the number
  squared_numbers.push(square)  # Push it into the squared_numbers array
end
```

In this example, the `.each` method needs to know what code to execute once per element in the array that it was invoked upon.

In order to give a method **code as input** (as opposed to _data as input_, for which we would use _arguments_), we use a **block**.

The syntax for giving a method a block is to put the `do` keyword after its name, and then put a matching `end` keyword on a line somewhere after that. Between the `do` and the `end`, we can write as many lines of code as necessary, and those lines of code will be passed to the method as input.

There is an optional syntax for blocks that contain only one line of code: rather than using `do` and `end`, you can just use `{` and `}`. So you might come across some Ruby that looks like this:

```ruby
our_numbers.each { |num| squared_numbers.push(num * num) }
```

I am not a big fan of such "concise" code. I prefer easily understood lines of code, even if there are more of them.

#### Chain

"Chaining" is usually used to refer to calling multiple methods in succession in the same expression, like so:

```ruby
geocoding_parsed_data.fetch("results").at(0).fetch("geometry").fetch("location").fetch("lng")
```

If the above reminds you of train, that's because it can often lead to a train wreck: when one step fails, perhaps by returning a `nil`, it can be hard to debug.

Prefer creating well-named intermediate variables over excessive method-chaining.

#### Class

#### Def

#### Div

#### Do

#### Each

#### Element

#### Expression

#### Fixnum

One of the built-in Ruby [classes](#class).

#### Float

One of the built-in Ruby [classes](#class).

#### Gem

#### Hash

One of the built-in Ruby [classes](#class). It is one of the two primary classes we use to represent **lists of things**. (The other one is [`Array`](#array).)

Ruby represents the list within curly brackets, with each element separated by a comma:

```ruby
{ :first_name => "Raghu", :last_name => "Betina", :role => "Instructor" }
```

Each element in a `Hash` consists of a **key/value pair**. The key comes first and is separated from the value by a `=>`, which is called a **hash rocket**.

Technically, the key can be any Ruby object, but we almost always use [`Symbol`s](#symbol), if we have a choice in the matter.

The value can can be any Ruby object — even another `Hash`, or an [`Array`](#array).

A blank instance of `Hash` can be created like any Ruby object, by calling `.new` on the class:

```ruby
h = Hash.new
```

or by using the curly bracket shorthand:

```ruby
h = {}
```

You can add elements to a hash with the `.store()` method, which takes two arguments; the first is the key you want to store an object under, and the second is the object you want to store:

```ruby
h.store(:first_name, "Raghu")
h.store(:last_name, "Betina")
h.store(:role, "Instructor")
```

There is also a square bracket shorthand for storing elements in a hash:

```ruby
h[:first_name] = "Raghu"
h[:last_name] = "Betina"
h[:role] = "Instructor"
```

You can also pre-populate the hash _in one fell swoop_ when you create it:

```ruby
h = { :first_name => "Raghu", :last_name => "Betina", :role => "Instructor" }
```

You can then access elements in the hash by key with the `.fetch()` method:

```ruby
h.fetch(:role) # => "Instructor"
```

There is also a square bracket shorthand for accessing elements:

```ruby
h[:role] # => "Instructor"
```

[Read more about hashes here.](https://guides.firstdraft.com/ruby-hashes.html)

#### Instance Variable

#### Key

#### Label

#### Loop

#### Method

#### Object

#### Operator

#### Render

#### Scrape

#### Source

#### String

One of the built-in Ruby [classes](#class).

#### Symbol

One of the built-in Ruby [classes](#class).

#### Table

#### Value

#### Variable
