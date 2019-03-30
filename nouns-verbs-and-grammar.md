# Nouns, Verbs, and Grammar

## You already know how to program

Programming is the art of getting a computer to do useful things with information.

If you think about it that way, then you already know how to program this computer:

![](/assets/youalreadyknow.png)

In the case of a calculator, the "information" is numbers and the "useful things" are adding, subtracting, multiplying, etc. Like any computer (or person), we get the calculator to do useful work by writing instructions that it can understand.

For example, if we press the keys <kbd>7</kbd> <kbd>×</kbd> <kbd>6</kbd> <kbd>=</kbd> (in that sequence), then the calculator will return `42` on the screen; but if we press the keys <kbd>x</kbd> <kbd>7</kbd> <kbd>=</kbd> <kbd>6</kbd>, then it won't.

- In the above example, `7` and `6` are known as **data**, or as I think of it, _nouns_.
- `x` and `=` are known as **methods**, or as I think of it, _verbs_.
- The order in which we press the keys is known as **syntax**, or as I think of it, _grammar_.
- Altogether, some data and some methods put together using correct syntax form an **expression**, or as I think of it, a _sentence_.
- Given a valid expression, the computer will process it and **return** a piece of useful data back to us.

A basic calculator's entire vocabulary consists of the following:

**Data**

<kbd>1</kbd> <kbd>2</kbd> <kbd>3</kbd> <kbd>4</kbd> <kbd>5</kbd> <kbd>6</kbd> <kbd>7</kbd> <kbd>8</kbd> <kbd>9</kbd> <kbd>0</kbd> <kbd>.</kbd>

**Methods**

<kbd>=</kbd> <kbd>+</kbd> <kbd>-</kbd> <kbd>×</kbd> <kbd>÷</kbd> <kbd>%</kbd> <kbd>±</kbd> <kbd>AC</kbd>

And there are only a few syntax rules:

- **Primary syntax**: two numbers separated by operator followed by <kbd>=</kbd>
- numbers can contain a single decimal point
- numbers can be modified by the plus/minus sign
- numbers can be modified by the percentage sign
- can press <kbd>AC</kbd> to reset

It's a very small language, but it demonstrates the same parts as any other programming language: **data**, **methods**, and **syntax**.

Got it? Good, because that's basically all that there is to any other programming language, too! It's just that its vocabulary will be bigger, and it will have a few more grammar rules.

## Ruby's vocabulary

Let's get started learning your second programming language — Ruby! As we now know, that means we need to familiarize ourselves with Ruby's **data**, **methods**, and the **syntax** for putting them together.

First of all, Ruby can work with many more kinds of data than just numbers. That's what makes it much more powerful than the calculator language. Ruby has:

- numbers
- text
- dates
- times
- true/false
- lists containing multiple pieces of data
- a lot more

Each kind, or **class**, of data has its own set of **methods** that it can perform. For example:

- numbers can do the usual computations
- two dates can tell you how far apart they are from one another
- lists can tell how you long they are, or sort themselves

Ruby is known as a "batteries included" language because it comes with _so many_ methods out-of-the-box, saving the programmer the trouble of having to re-invent the wheel.

Finally, *we can even make up our own nouns and verbs* and add them to the language. For example, we can create a data type `Venue`, teach it how to calculate the average rating from its reviewers, add that method to its instruction set, and then use it whenever we want.

One of the best things about Ruby is its wonderful **open-source** community: programmers very often share these new classes that they write with one another, making the language ever easier to use and more powerful!

## Ruby's primary syntax

So, in terms of **data** and **methods**, Ruby comes with a powerful set out-of-the-box *and* is infinitely extensible! That's good news. Here's even more good news: to access all of this power, the **primary syntax** is straightforward. It looks like this: `some_object.some_method`

Here's a real example:

```ruby
"hello world!".upcase
```

Here, you try it in the interactive Ruby sandbox[^replit] below:

[^replit]: The interactive Ruby playgrounds that are embedded in these readings are hosted on a service called repl.it. If you see a page asking you to sign up or sign in, then click the <i class="fab fa-github fa-fw"></i> icon to sign in using your GitHub account. After signing in for the first time, you might have to refresh this page in your browser to get it to load.

<iframe frameborder="0" width="100%" height="600px" src="https://repl.it/student_embed/assignment/3043043/c68c4738e364e9b4dbb0b7cf4c224003"></iframe>

Yay[^tradition]! What just happened?

[^tradition]: It is [a time-honored tradition](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program){:target="_blank"} that the very first thing a programmer does in a new language is print out "Hello, World!" Congratulations — you're now one of us 🙌🏾

The primary way to write an expression in Ruby is: `object.method`. We ask the _thing_, or noun, on the left side of the dot to perform the _action_, or the verb, on the right side of the dot. The computer then evaluates that expression and returns a new piece of data in its place (just like with the calculator).

In this case, we asked `"hello world!"`, which is a `String` (Ruby's name for a piece of text[^string_name]), to `upcase` itself, which it (very) happily does, and we're left with `"HELLO WORLD!"` at the end of the day.

[^string_name]: The name "string" is used in pretty much every programming language for the datatype that holds a piece of text, and refers to a string of _characters_; a holdover from back when we used to have to worry about memory and had a separate datatype for an individual character. Now we usually don't have to think about individual characters anymore, but the name "string" stuck with us.

## Every class has different methods

Different **classes** can perform different **methods**. Try the following:

```ruby
7.swapcase
```

<iframe frameborder="0" width="100%" height="600px" src="https://repl.it/student_embed/assignment/3043048/e3a0f724d73a975907c6441b855876aa"></iframe>

Aha! If you were typing out every expression and running it, then you should have run into your very first error message! 🎉

(If you weren't typing out every expression, then you're doing this all wrong. If you're just reading, you won't be successful at learning programming; you have to _do_ in order to build up some muscle memory. It's all about practice.)

Error messages can look scary, but one of **the most important skills you have to develop** when learning to program is to **not panic** when you see them. Slow down, read it carefully, and see if you can make any sense of it at all. Over time, you will find that they are _very_ helpful — and you will miss them when something is going wrong *silently*.

So, what do you think

```bash
undefined method `swapcase' for 7:Integer
(repl):1:in `<main>'
```

might mean?

In this case, it is saying: "Hey, friend — there's no method called 'swapcase' for 7, which is an integer. Sorry." Fair enough.

The bottomline is: at all times as you are writing Ruby, you should be thinking: **What class of object do I have to work with?** **What methods am I allowed to call on this kind of object?** Then, the syntax itself is simple — `object.method`!

## Arguments

Alright, so the **primary syntax** in Ruby is straightforward — `object.method`. However, there's a wrinkle: some methods require additional inputs. For example, there is a method called `gsub` which we can call on `String`s, which will substitute characters with other characters. Try it:

```ruby
"Hello".gsub("l", "z")
```

<iframe frameborder="0" width="100%" height="600px" src="https://repl.it/student_embed/assignment/3044475/1042c1330f295bf2626ebc732be74e2b"></iframe>

`gsub` is short for "globally substitute", because it will replace _all_ occurrences of one _substring_ with another _substring_.

In order to do its job, the `gsub` method needs to know what substring to get rid of and what to replace it with. So we give it inputs, or **arguments**, which must come in parentheses _immediately_ following the method. If the method takes multiple arguments, as `gsub` does, then they are separated by commas.

In reality, `gsub` is more often used to do things like removing illegal characters from usernames before saving:

```ruby
"D+h+H".gsub("+", "")
```

(`""` is an empty string, so all `+`s get replaced with nothing.)

### One of the only places that whitespace matters

Ruby is, generally, very permissive about whitespace; unlike some other languages (e.g. Python) where indentation can change the entire meaning of the program.

So, for example, whether you have spaces between arguments doesn't matter; these two are equivalent:

```ruby
"Hello".gsub("l", "z")
"Hello".gsub("l","z")
```

(The most common style is to have one space after each comma.)

However, one situation that whitespace does matter is: **do not put a space between a method and the parentheses that surround its arguments**.

It's a very easy mistake to make, so I just wanted to warn you early so you can develop good muscle memory:

```ruby
"Hello".gsub("l", "z") # good
"Hello".gsub ("l", "z") # bad!
```

## Code comments

A question for the ages: what do you call this symbol: `#`? The number sign? The pound sign? The hashtag? The waffle?

For the purposes of this text, I'm going to refer to it as an [octothorpe](https://en.wiktionary.org/wiki/octothorpe){:target="_blank"}.

The octothorpe is used quite a bit in Ruby. You can see one important way in the code block above, where I said `# bad!` after some offending code. That is known as a "code comment". The Ruby interpreter, when it sees the `#`, will ignore it and everything that comes after it; allowing us to leave notes to ourselves and to each other. Use comments liberally.

Another nice trick is: when experimenting with some code and it's not working, just comment it out and try a different approach on the next line. That way you can keep the old code around for reference without having to delete it, but it won't break the program.

## Variables are boxes

Now that you've seen arguments, you know the full **primary syntax** of Ruby. No kidding: crafting expressions with `object.method(argument1, argument2, ...)` is the *vast* majority of what we'll be doing. That's it.

However, so far we haven't been doing much with the **return value** of each expression. We've just been reading it, and then dropping it on the ground. Programs get interesting only when we start to take the return value of one expression and feed it into the next method. That's how we craft novel, useful applications from the basic building blocks of Ruby.

So: let's start to save our return values instead of dropping them on the ground. We do this using **variables**. Try the following:

<iframe frameborder="0" width="100%" height="600px" src="https://repl.it/student_embed/assignment/3044609/57a19463be616e484b188e67bb75a7d0"></iframe>

So, in addition to `object.method`, **the syntax you need to know like the back of your hand is**

```ruby
storage_box = the_final_value.resulting_from_this(expression).will_be_stored
# This code won't actually work
```

*First*, the expression on the right will be evaluated until there are no instructions left and there's just a piece of data remaining.

*Then*, the value will be placed in a variable called `storage_box`, which will be created if it doesn't exist, or will have its value replaced if it does.

Most programs are just a long succession of statements where we do some work with `object.method` and store the result in some variable, then we do some more work on that variable and store the result in yet another variable, and a hundred steps later we've produced our final result and we display that to our user:

```ruby
user_input = "D+h+H"
input_without_pluses = user_input.gsub("+", "")
downcased_input = input_without_pluses.downcase
"dhh" == downcased_input
# if true, choose another username!
```

When you are choosing your variable names, there are some rules:

- names can only contain **lowercase** letters, numbers, and underscores
- names cannot begin with a number

Rubyists strive to choose descriptive variable names, no matter how long they are, so that the code reads almost like English — avoid naming your variables `x`, `y`, and `z`. Use underscores to separate words in multiple word variable names.

## Conclusion

That's it for the primary syntax of Ruby!

```
storage_box = object.method(argument1, argument2, ...)
```

Now, we need to spend some time *expanding our vocabulary*. Let's start with [the most fundamental built-in classes that Ruby gives us](fundamental-classes.md).

## Variables

Now that you've seen arguments, you know the full **primary syntax** of Ruby. No kidding: `object.method(argument1, argument2, ...)` is the *vast* majority of what we'll be writing. That's it.

"But wait!," you say, "what about when I do math like `7 * 6`? That is clearly not `object.method`." A very good question. Try this instead: `7.*(6)` What?!

Why does this work? `*` is the name of a method on the `Fixnum` class, which takes an argument of another `Fixnum`, and returns the product of the two. 😳💥😲

When [Yukihiro Matsumoto](https://twitter.com/yukihiro_matz) designed the Ruby language, his goal was "developer happiness" (which was radical at that time, 1993, when most languages were geared for computer efficiency).

He knew that if he made developers type `7.*(6)` every time they wanted to multiply two numbers, they would not be happy campers. So he included a few bits of "syntactic sugar", or shortcuts, that boil down to `object.method` under the hood, but allow us to retain our sanity while typing. Phew.

One last thing: you can **chain** methods, like so:

```ruby
"D+h+H".gsub("+", "").downcase
```

Ruby evaluates the expression from left to right, replacing each `object.method` expression with the `object` that it returns and then evaluating the next `object.method`.

So you have to be careful and make sure that the `object` that the first `object.method` returns matches up with the second `method.` **What class of object do I have?** **What methods can I call on this kind of object?**



[^1]: [MDN HTML element reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)

[^2]: [MDN CSS reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference)

[^3]: Read about [Complex Selectors](http://learn.shayhowe.com/advanced-html-css/complex-selectors/), or play a game to learn them: [CSS Diner](https://flukeout.github.io/)
