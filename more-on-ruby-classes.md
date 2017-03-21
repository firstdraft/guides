# Ruby Classes

## Modeling real world things

We can *model* a person pretty well with an `Array`:

```ruby
a = Array.new # This is the longhand for a = []
a.push("Raghu")
a.push("Betina")
a.push("Instructor")

a # => ["Raghu", "Betina", "Instructor"]

a[1] # => "Betina"
a.class # => Array
```

And we can model a person even better with a `Hash`:

```ruby
h = Hash.new # This is the longhand for h = {}
h[:first_name] = "Raghu"
h[:last_name] = "Betina"
h[:role] = "Instructor"

h # => { :first_name => "Raghu", :last_name => "Betina", :role => "Instructor" }

h[:last_name] # => "Betina"
h.class # => Hash
```

But we can do even better than a Hash. We can define *our own class* to represent people:

```ruby
class Person
end
```

And we can declare what attributes a person can have:

```ruby
class Person
  attr_accessor :first_name
  attr_accessor :last_name
  attr_accessor :role
end
```

And now the `Person` class is a first-class citizen in the language, just like `Array` and `Hash`:

```ruby
c = Person.new
c.first_name = "Raghu"
c.last_name = "Betina"
c.role = "Instructor"

c.last_name # => "Betina"
c.class # => Person
```

There are a few reasons I like using classes more than Hashes to model things, but here is the big one: in addition to just storing a list of attributes about a thing, we can also *add behavior*. For example,


```ruby
class Person
  attr_accessor :first_name
  attr_accessor :last_name

  def full_name
    return self.first_name + " " + self.last_name
  end
end
```

Now, in addition to being able to store data (first and last names), I can ask any `Person` to compute its full name:

```ruby
hs = Person.new
hs.first_name = "Homer"
hs.last_name = "Simpson"

"Hello, #{hs.full_name}!" # => "Hello, Homer Simpson!"
```

Two new keywords to note:

 -  I used the `return` keyword to signify what value I wanted to replace `hs.full_name` in the original expression after it's been evaluated.
 - I used the `self` keyword to refer to the object who was asked to calculate its full name, since I can't know in advance what (if any) variable name will be used.

Here's a slightly more involved example:

```ruby
class Person
  attr_accessor :birthdate

  def age
    dob = Date.parse(self.birthdate)
    now = Date.today
    age_in_days = now - dob
    age_in_years = age_in_days / 365

    return age_in_years.to_i
  end
end
```

Now every `Person` that we create will have the ability to compute their age based on their own dob attribute:

```ruby
hs = Person.new
hs.birthdate = "April 19, 1987"

hs.age # => 29, as of this writing
```

So, rather than using a `Hash` to model everything, it's much more powerful to create classes for each kind of thing, and then empower them with *behavior* (methods) in addition to information.

## Inheritance

When you define new classes, you can choose to inherit all the power of a "parent" class, and then add some custom behavior:

```ruby
class Instructor < Person
  attr_accessor :role
end

class Student < Person
  attr_accessor :grade
end
```

`Instructor`s and `Student`s can do everything people can, and a little bit more.

Creating the first individual **instance** of the `Instructor` class:

```ruby
person1 = Instructor.new
person1.first_name = "Raghu"
person1.last_name = "Betina"
person1.role = "Lecturer"
```

Creating the second individual instance of the `Instructor` class:

```ruby
person2 = Instructor.new
person2.first_name = "Arjun"
person2.last_name = "Venkataswamy"
person2.role = "Faculty Coach"
```

Creating the first individual instance of the `Student` class:

```ruby
person3 = Student.new
person3.first_name = "Trenton"
person3.last_name = "Arthur"
person3.grade = "A"
```

Creating the second individual instance of the `Student` class:

```ruby
person4 = Student.new
person4.first_name = "Tom"
person4.last_name = "Besio"
person4.grade = "Incomplete"
```

Now we can use them:

```ruby
person1.full_name # => "Raghu Betina"
person1.role # => "Lecturer"
person2.full_name # => "Arjun Venkataswamy"
person2.role # => "Faculty Coach"
person3.full_name # => "Trenton Arthur"
person3.grade # => "A"
person4.full_name # => "Tom Besio"
person4.grade # => "Incomplete"
```

What would happen if I tried doing `person4.role`? How about `person1.grade`? Why? What would the error message be?

## Using our own classes

We usually store classes that we write in the `app/models` folder. For example, if you create a file in that folder called `person.rb` with the following:

```ruby
class Person
  attr_accessor :first_name
  attr_accessor :last_name
  attr_accessor :birthdate

  def full_name
    return self.first_name + " " + self.last_name
  end

  def age
    dob = Date.parse(self.birthdate)
    now = Date.today
    age_in_days = now - dob # Returns a Rational number
    age_in_years = age_in_days / 365

    return age_in_years.to_i
  end
end
```

You can now use the `Person` class from anywhere in the app: from within any controller, any view template, in the `rails console` -- or even from within another model.

Ruby is called an Objected Oriented (OO) language because we always strive to organize our code into descriptive classes and methods, rather than just using Hashes and Arrays for everything.

For example, Rubyists much prefer to define the `Person` class above and then

```ruby
hs = Person.new
hs.first_name = "Homer"
hs.last_name = "Simpson"

"Hello, #{hs.full_name}!" # => "Hello, Homer Simpson!"
```

Rather than

```ruby
h = { :first_name => "Homer", :last_name => "Simpson" }

"Hello, #{hs.first_name} #{hs.last_name}!" # => "Hello, Homer Simpson!"
```

even though the two are functionally equivalent, and the second is even a bit more concise.

By encapsulating the logic of how to compute `full_name` in the class definition, I make it much easier to re-use elsewhere and share.

## Where have we seen this before?

It might now make a bit more sense what we were doing when we created our controllers while learning RCAV:

```ruby
# config/routes.rb

get("/rock", { :controller => "games", :action => "play_rock" })

# app/controllers/games_controller.rb

class GamesController < ApplicationController
  def play_rock
    @computer_move = ["rock", "paper", "scissors"].sample

    render("games/play_rock.html.erb")
  end
end
```

In `routes.rb`, we tell Rails to listen for requests for "/rock", and when it hears one, run the `play_rock` method on an instance of `GamesController`. Behind the scenes, Rails would do something like

```ruby
g = GamesController.new
g.play_rock
```

when someone visits "/rock". That's why we have to be so careful when we're [connecting the RCAV dots](rcav-flowchart.md); otherwise, Rails can't locate the method to run.

`GamesController` inherits from `ApplicationController`, which is a pre-written class we get from Rails.

It has lots of powerful methods that deal with web requests, like `render()`, which knows how to parse a `.html.erb` embedded Ruby view template and process it into pure HTML suitable for a browser to display.

Thankfully, we inherit all that functionality for free from Rails, instead of having to write it ourselves! We can instead focus on modeling the problem that we want to solve with our app, rather than worrying about all that plumbing.