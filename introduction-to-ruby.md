# Introduction to Ruby

## Getting Started

This is a minimal introduction to the Ruby programming language, intended to get you far enough to begin using the Ruby on Rails web application framework.

To get started, visit [this page](https://github.com/appdev-projects/ruby-intro) and follow the instructions to download the code to your Cloud9 workspace.
  
Once you've downloaded the starter code and are at a Terminal prompt within the project folder, type the following command and then press <kbd>return</kbd>:

```
rails console
```

You should end up at a prompt that says `[1] pry(main)> ` and looks something like this:

![](/assets/ruby-intro-launch-rails-console.png)

You have launched an app called the Rails Console that is an interactive playground; it allows you to try out the Ruby language as you read about it below.

As you read, try out each new Ruby concept at the prompt. Have fun!

## What is Ruby?

### The shortcomings of HTML

What is Ruby? To answer that, first consider what we can and can't do with plain old HTML:

We can:

 - Give data structure with HTML.
 - Give data style with CSS.

But we can't:

 - Perform **computations** on data.
  - For example, `24 × 365`, or how many hours are there in a year? HTML cannot answer this question.
 - Have **dynamic content** like a random word that we didn't type into the source code of the page ourselves.
  - For example, did a computer opponent choose rock, paper, or scissors?
 - Display messages only if certain **conditions** are met.
  - For example, "You win!" if you chose rock and the opponent chose scissors.

Basically, HTML by itself can only produce static, unchanging websites that look the same to all visitors, and all you can do on them is click around them and read them. It's a *markup language* for content.

This might be fine for some informational sites (like the location, hours, and menu of a restaurant), but it will clearly not do for the kind of tailored, interactive web applications that we want to build (like GrubHub, where we can leave reviews or order delivery).

So, we need to learn a *general purpose language* in addition to HTML, so that we're not limited to just formatting static data. We want to save information on behalf of our users, tailor the experience for them based on who they are, and much more.

### Ruby

There are many general purpose programming languages, but the one that we're going to learn is called Ruby. It can do all three of the above things, and much more.

Let's spend a few minutes just getting our hands dirty with Ruby before we describe the theory behind it.

Try out the commands below in your `rails console`. Type each one after the prompt that says `pry(main)>` and press <kbd>return</kbd> after each line, and you will see how Ruby interprets each expression on the next line after the `=>`.

#### Simple math

```ruby
24 * 365
```

If everything went well, you should see something like this:

```bash
[1] pry(main)> 24*365
=> 8760
```

Now try all the below:

#### Random numbers

```ruby
rand(6)
```

Try it again  (you can just press the up arrow to get back your last command):

```ruby
rand(6)
```

Try it again if you have to until you get a different number 🎲🎲

#### Getting un-messed up

This might be a good time to point out that if you make a mistake while entering an expression into `rails console` — let's say for example that you forgot a closing parenthesis — it's possible to get into a *weird state* where you press <kbd>return</kbd> and nothing happens. It's still waiting for that closing parenthesis, and then you start typing more commands, and it gets confused, and then you get confused.

If something like this happens, press <kbd>Ctrl</kbd>+<kbd>C</kbd> to break out of the weird state and reset back to a clean state. You can then use the up arrow to scroll back through your history and try to fix the malformed command.

#### Comparison statements

(Only type the stuff before the `#`; the stuff after are known as *code comments*, and are just there as notes to ourselves. They have no effect on the program.)

```ruby
1 < 2           # "1 is less than 2"
2 < 1           # "2 is less than 1"
24*365 > 10000  # There are more than 10,000 hours in a year
1 == 1          # "1 is equivalent to 1"
1 == 2          # "1 is equivalent to 2"
1 != 1          # "1 is NOT equivalent to 1"
1 != 2          # "1 is NOT equivalent to 2"
```

#### Strings

Unlike your phone's calculator app, Ruby can work with many more data types than just numbers. Most importantly, Ruby can work with text, which we wrap inside quotation marks and refer to as "strings" (of characters):

```ruby
"hello"
```

That wasn't very interesting, but note that if you left out the quotation marks, Ruby gets confused:

```ruby
hello
```

Your very first error message! You are going to see a *lot* of these — 99% of developing software is trying to figure out error messages. They might look scary at first, but later on they will become helpful old friends!

Anyway, let's do something more interesting with strings:

```ruby
"Hello".length
"Hello".downcase
"Hello".upcase
"Hello".reverse
```

#### Variables

Remember, you can use your up and down arrows to scroll through your command history. That would have saved you from retyping `"Hello"` over and over.

But Ruby has a more important way to save that piece of data: we can create a box to hold it and give that box a name, like so:

```ruby
s = "Hello" # Create a box, label it `s`, and store "Hello" in it
s           # Retrieve the value in `s`
s.capitalize
s.reverse
s.upcase
```

You could also throw away what you have in the box labeled `s` and put in something new:

```ruby
s = "hi"
s
s = 60 * 60
s
```

You could even replace the value in the box with an updated version of the old value, because the instructions on the right side of the equals sign are executed before the throwing away happens:

```ruby
s = "hi"
s
s = s.capitalize
s
```

And you can create as many of these boxes as you want:

```ruby
a = "hi"
b = "there"
c = "world"
a
b
c
```

(Note that here we are using a single-equals sign, `=`, the **variable assignment operator**. Above, while doing comparisons, we used the *completely and totally different* double-equals sign, `==`, the **logical equivalence operator**. Mixing up these two operators is a very easy mistake to make, and even experienced devs make it all the time — watch out.)

#### Putting it together

Believe it or not, from these simple building blocks, we can build up much of what happens on the web today. For example, when Twitter tries to make sure that no one can sign up using the same username as [David Heinemeier Hansson](https://twitter.com/dhh), the creator of Ruby on Rails, even if they try to be sneaky and use mixed-case, they would do something like

```ruby
user_input = "DhH"
existing_username = "dhh"
user_input == existing_username # double-equals, not single!
user_input.downcase == existing_username
```

Remember our Photogram Database exercise? Figuring out which photos were on a user's timeline — a seemingly complicated task — ended up being a long sequence of small and simple steps, like the ones above. Most applications are. It was tedious for us to do it by hand, though, so now we just need to learn enough Ruby vocabulary to teach the computer to do it for us. We'll spend the next several lessons learning just that.

### Rails

Before we dig in to Ruby, let's talk a little bit more about Ruby ***on Rails***.

Ruby, as a general purpose language, can be used for just about anything — producing music[^1], flying drones[^2] — you name it. What *we* want to do with it, though, is produce useful HTML pages and send them to our users.

“Ruby on Rails” is just a name for a bunch of pre-written Ruby code — like what you downloaded when you began this project. It already includes, out of the box, all of the plumbing involved with delivering the output of Ruby programs to users through browsers.

That way, instead of re-inventing the wheel for all that first, we can just get right down to the fun stuff — bringing our ideas to life!

Next, let's learn the [Primary Syntax of Ruby](primary-syntax.md).

[^1]: [http://sonic-pi.net/](http://sonic-pi.net/)

[^2]: [http://artoo.io/](http://artoo.io/)
