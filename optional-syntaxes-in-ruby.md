# Optional Syntaxes in Ruby

Ruby, unlike many other languages, often supports multiple syntaxes to achieve the same thing. This is both good and bad. It's good because it lets us choose a style that we are most comfortable with, but it's bad because we need to learn to at least recognize multiple styles so that we can read other people's code.

Here are a few optional syntaxes to become familiar with:

## Parentheses around arguments

When we call a method that has arguments, we put the arguments in parentheses (`()`) immediately next to the method name (with no space between the method name and the opening parenthesis):

```ruby
"hello".gsub("l", "z")

# => "hezzo"
```

Ruby will allow you to, optionally, drop the parentheses around arguments:

```ruby
"hello".gsub "l", "z"

# => "hezzo"
```

**Don't mix these two by putting a space before parentheses!**

```ruby
# Don't do this

"hello".gsub ("l", "z")
```

I like to include the parentheses around arguments because it makes it clear what's what, _especially_ when you are chaining multiple methods together. The one time that I usually drop the parentheses is if I am `puts`ing or `ap`ing:

```ruby
# Rather than

ap("Hi there")

# I will usually do this instead:

ap "Hi there"
```

## Curly brackets around hash arguments



## New Hash Syntax

Consider a `Hash`:

```ruby
{ :fruit => "banana", :sport => "hockey" }
```

You can write the same thing as:

```ruby
{ fruit: "banana", sport: "hockey" }
```

In other words, if the key in a key-value pair in a hash is a `Symbol`, you can move the colon (`:`) from the front of the symbol to the back of the symbol, and get rid of the hash rocket (`=>`).

The Rails team has adopted the new hash syntax as their default, so when you're reading the Rails Guides, you will often see things like this:

```ruby
class Holiday < ApplicationRecord
  validates :name, uniqueness: { scope: :year,
    message: "should happen once per year" }
end
```

Consider the following Hash:

```ruby
{ "color" => "pink", "dessert" => "cookies" }
```

Can we do the same trick and write this as

```ruby
{ "color": "pink", "dessert": "cookies" }
```

No! This optional hashshortcut syntax is **only useable when the keys are symbols** — not strings or anything else.



## Single line blocks

