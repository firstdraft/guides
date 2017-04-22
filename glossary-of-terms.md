# Glossary of Terms

#### Argument

An input to a [method](#method):

```ruby
"well, hello!".gsub("ll", "z") # => "wez, hezo!"
```

In the example above, the strings `"ll"` and `"z"` are both arguments to the method `gsub`.

Arguments are supplied to methods within parentheses immediately following method names, and if there are multiple arguments, then they are separated by commas.

Don't put a space between the method's name and the parentheses that contain its arguments!

Ruby does allow you to, optionally, omit the parentheses; and some Rubyists do prefer that style. So when you are reading Ruby around the internet, you will encounter things like this:

```ruby
[5, 4, 7, 4, 11].count 4
```

rather than

```ruby
[5, 4, 7, 4, 11].count(4)
```

It's just a matter of taste which one you use, but definitely don't use both parenthese _and_ the space like this

```ruby
[5, 4, 7, 4, 11].count (4) # bad!
```

I, personally, prefer using the parentheses around arguments to keep it clear what goes with what, especially when you start to use more than one method on the same line.


#### Array

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

#### Float

#### Gem

#### Hash

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

#### Symbol

#### Table

#### Value

#### Variable
