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

I, personally, prefer using the parentheses around arguments to keep it clear what goes with what, especially when you start to use more than one method on the same line.


#### Array

One of the core Ruby [classes](#class).

#### Block

#### Box

#### Chain

#### Class

#### Def

#### Div

#### Do

#### Each

#### Element

#### Expression

#### Fixnum

One of the core Ruby [classes](#class).

#### Float

One of the core Ruby [classes](#class).

#### Gem

#### Hash

One of the core Ruby [classes](#class).

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

One of the core Ruby [classes](#class).

#### Symbol

One of the core Ruby [classes](#class).

#### Table

#### Value

#### Variable
