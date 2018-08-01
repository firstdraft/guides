# Optional Syntaxes in Ruby

Ruby, unlike many other languages, often supports multiple different syntax styles to achieve the same thing. This is both good and bad. It's good because it lets us choose a style that we are most comfortable with, but it's bad because we need to learn to at least recognize all of the styles so that we can read other people's code.

Here are a few optional syntax styles to become familiar with:

## No parentheses around arguments

When we call a method that has arguments, we put the arguments within parentheses (`()`) immediately next to the method name (with no space between the method name and the opening parenthesis):

```ruby
"hello".gsub("l", "z")

# => "hezzo"
```

Ruby will allow you to, optionally, drop the parentheses around arguments:

```ruby
"hello".gsub "l", "z"

# => "hezzo"
```

It's important to remember **not to mix these two by putting a space before parentheses!**

```ruby
# If you're going to use parens, don't also have a space

"hello".gsub ("l", "z") # bad
```

I like to include the parentheses around arguments because it makes it clear what's what, _especially_ when you are chaining multiple methods together. The only time that I drop the parentheses is if I am `puts`ing or `ap`ing:

```ruby
# Rather than

puts("Hi there")

# I will usually do this instead:

puts "Hi there"
```

## Curly brackets around hash arguments

Consider a hypothetical method that accepts a Hash as its last argument:

```ruby
some_method("first_argument", 2, { :this => "argument", :is => "a Hash" })
```

How many arguments does the above method have? You might be tempted to say four or even six if you just count, but really it's three: a string is first, an integer is second, and the entire hash (`{ :this => "argument", :is => "a Hash" }`) is the _third_ and final argument.

In the case that a Hash literal is being used as the last argument to a method, you can optionally drop the curly brackets around it:

```ruby
some_method("first_argument", 2, :this => "argument", :is => "a Hash")
```

Now it _really_ looks like the method is taking four arguments, but it's not; Ruby can figure out from the hash rockets that the final two things are really just one Hash.

**Note that you can _only_ drop the curly brackets around a Hash in this one, very specific case** — if the Hash is the _last_ argument to a method. So this:

```ruby
my_hash = { :fruit => "banana", :sport => "hockey" }

# Creating a Hash and storing it in a variable
```

is **not** the same as this:

```ruby
my_hash = :fruit => "banana", :sport => "hockey"

# Nonsensical, as far as Ruby is concerned.
```

## New Hash Syntax

Consider a `Hash`:

```ruby
{ :fruit => "banana", :sport => "hockey" }
```

We can also (as of Ruby version 1.9) write the same thing as:

```ruby
{ fruit: "banana", sport: "hockey" }
```

In other words, if the key in a key-value pair in a hash is a `Symbol`, you can move the colon (`:`) from the beginning of the symbol to the end of the symbol, and get rid of the hash rocket (`=>`). This is known as the "new hash syntax" (even though Ruby 1.9 is pretty old by now).

Consider the following Hash:

```ruby
{ "color" => "pink", "dessert" => "cookies" }
```

Can we do the same trick and write this as:

```ruby
{ "color": "pink", "dessert": "cookies" }
```

No! This new hash syntax is **only useable when the keys are symbols** — not strings or anything else.

## Putting it all together

Consider one of our routes:

```ruby
get("/photos", { :controller => "photos", :action => "index" })
```

Since the keys are symbols, we can use the new hash syntax:

```ruby
get("/photos", { controller: "photos", action: "index" })
```

Since the Hash is the final argument to the `get()` method, we can drop the curly brackets:

```ruby
get("/photos", controller: "photos", action: "index" )
```

And since there are no order-of-operations concerns, we can drop the parentheses around the arguments:

```ruby
get "/photos", controller: "photos", action: "index"
```

Much more concise! Again, I personally prioritize readability far above brevity, so I like making things explicit rather than concise. However, when you are reading Ruby code out in the wild (on Stack Overflow or GitHub), you will most often encounter code using all of these shortcuts, so you have to know how to read it.

Most importantly, the Rails team has adopted the above optional syntaxes as their default, so when you're reading the [Rails Guides](https://guides.rubyonrails.org/active_record_validations.html#uniqueness), you will often see things like this:

```ruby
class Holiday < ApplicationRecord
  validates :name, uniqueness: { scope: :year, message: "should happen once per year" }, presence: true
end
```

What's going on here? You just have to unwind each optional syntax one by one to get to something more familiar.

First of all, they have dropped the parentheses around the arguments to the `validates()` method. We can replace them:

```ruby
class Holiday < ApplicationRecord
  validates(:name, uniqueness: { scope: :year, message: "should happen once per year" }, presence: true)
end
```

Next: whenever you see a colon at the end of a token, you know it's the new Hash syntax. So we can unwind it by moving the colons to the beginning and putting back the Hash rockets:

```ruby
class Holiday < ApplicationRecord
  validates(:name, :uniqueness => { :scope => :year, :message => "should happen once per year" }, :presence => true)
end
```

Notice that I didn't (and can't) move the colon in `:name` — it's already at the beginning, and this Symbol is not being used as the key in a Hash. It is simply the first argument to the `validates` method. Similarly, the  Symbol`:year` is the _value_ associated to the key `:scope`, so we leave it alone.

Next: the second and last argument to the `validates()` method is a Hash with two keys (`:uniqueness` and `:presence`), so the Rails Guides dropped the curly brackets around it. We can put them back:

```ruby
class Holiday < ApplicationRecord
  validates(:name, { :uniqueness => { :scope => :year, :message => "should happen once per year" }, :presence => true })
end
```

Now that we've fully unwound the optional syntaxes, it's easier to see that:

 - The `validates()` method is taking two arguments; the first is a Symbol and the second is a Hash.
 - The value associated with the `:uniqueness` key is itself another, nested, Hash: `{ :scope => :year, :message => "should happen once per year" }`.
 - That Hash has two keys in it: `:scope` and `:message`.
 - We cannot drop the curly brackets around `{ :scope => :year, :message => "should happen once per year" }` because **it is not the last argument to a method** — it is the value associated to the key `:uniqueness` in a parent hash. If we tried to drop them, we'll run into problems:
 
    ```ruby
    class Holiday < ApplicationRecord
      validates(:name, { :uniqueness => :scope => :year, :message => "should happen once per year", :presence => true })
    end
    ```
    
    Ruby can't make sense of `:uniqueness => :scope => :year`, and can't tell which things are in the inner hash vs. the outer hash.

So: don't fret when you see seemingly unfamiliar syntax like `scope: :year` — it's nothing new, it's just a different style. You've got the tools you need to understand any Ruby you encounter.

## Single line blocks

Often, we only have one line of code within our `do`/`end` blocks:

```ruby
5.times do
  ap "hi!"
end
```

In this case, you can use a shorthand:

```ruby
5.times { ap "hi!" }
```

This gets confusing, because now we're overloading the curly brackets (`{}`) for more than one purpose: Hash literals _and_ blocks. However, it's a very common style so you should get used to figuring out which one it is from the context. If the curly brackets are next to a method and there are no key/value pairs, then it's a block, not a Hash. 