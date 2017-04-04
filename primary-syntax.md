# Ruby Primary Syntax

## Nouns, Verbs, and Grammar

### Calculators

When we program, we generally have some **data** (or information) that's important to us; and we want to do something useful with it.

Let's consider a computer that you already know how to program:

![](/assets/calculator.gif)

When we're using (or programming) a calculator, our data are numbers and we want to tell the processor to add, subtract, multiply, and perform other calculations on them.

When we write an **expression** in the calculator language, we need to put together **data** and **instructions** in an order that makes sense; for example, if we press the keys <kbd>7</kbd> <kbd>×</kbd> <kbd>6</kbd> <kbd>=</kbd> in that sequence, we will see the intended output in the screen.

We refer to "an order that makes sense" as the language's **syntax**, or grammar. In the calculator language, <kbd>×</kbd> <kbd>7</kbd> <kbd>=</kbd> <kbd>6</kbd> would not be valid syntax.

A basic calculator's entire programming language vocabulary consists of the following:

**Data**

<kbd>1</kbd>
<kbd>2</kbd>
<kbd>3</kbd>
<kbd>4</kbd>
<kbd>5</kbd>
<kbd>6</kbd>
<kbd>7</kbd>
<kbd>8</kbd>
<kbd>9</kbd>
<kbd>0</kbd>
<kbd>.</kbd>

**Instructions**

<kbd>=</kbd>
<kbd>+</kbd>
<kbd>-</kbd>
<kbd>×</kbd>
<kbd>÷</kbd>
<kbd>%</kbd>
<kbd>±</kbd>
<kbd>AC</kbd>

and there are only a few **syntax** rules:

 - **Primary syntax**: two numbers separated by operator followed by <kbd>=</kbd>
 - numbers can contain a single decimal point
 - numbers can be modified by the plus/minus sign
 - numbers can be modified by the percentage sign
 - can press <kbd>AC</kbd> to reset

It's a very small language, but it demonstrates the same parts as any other programming language: **data**, **instructions**, and **syntax**.

I think of them as *nouns*, *verbs*, and *grammar*. For each language we want to learn, we just have to learn what *things* we can work with, what we can *do* with those things, and how to put together valid *expressions* to tell the processor to do them.

### HTML

Let's consider a slightly more complicated language that you already know: HTML.

 - What kind of data do we work with in HTML?
 - What kind of instructions do we give the processor (the browser) to handle our data?
 - What syntax rules are there?

It seems to me that we have:

**Data**

Arbitrary text content.

**Instructions**

`h1` `h2` `h3`, `h4`, `h5`, `h6`, `p`, `ul`, `ol`, `li`, `img`, `src`, `a`, `href`, `link`, etc

**Syntax**

```html
<li>
  <a href="details.html">
    Raghu Betina
  </a>
</li>
```

 - **Primary syntax**: `<`, element name, `>`, content, `</`, element name, `>`
 - elements can be nested within other elements
 - opening tags can contain attributes, which are separated from their values by a `=` and the values are wrapped in `""`

That's it! There are maybe even less syntax rules than the calculator language, so it didn't take us long to grasp the essence of it.

There are, however, more available instructions than in the calculator language (although surprisingly few[^1]). So we will have to still spend some time *expanding our vocabulary* before we master all of HTML.

### CSS

CSS follows a similar pattern; the **primary syntax** is quite approachable:

```css
.fanciness {
  text-decoration: underline;
}
```

We put our class name (preceded by a dot), followed by curly braces, followed by a list of property-value pairs that we want in our style rule.

CSS, though, does have a *lot*[^2] of available instructions. It also has a significant variety of available syntaxes to give you fine-grained control over which elements on the page are targeted[^3].

So to master CSS, we would have to spend a lot of time both *expanding our vocabulary __and__ learning more advanced syntax rules*.

### Ruby

Finally, let's think about how Ruby compares.

In terms of **data**, Ruby can work with:

 - numbers like calculators
 - text like HTML
 - a lot more, including
   - dates
   - times
   - lists

Each class of data has its own set of **instructions** that it can perform:

 - numbers can do the usual computations
 - two dates can tell you how far apart they are from one another
 - lists can tell how you long they are or sort themselves

Ruby is known as a "batteries included" language because it includes so many instructions out-of-the-box, saving the programmer the trouble of having to re-invent the wheel.

Finally, *we can even make up our own nouns and verbs* and add them to the language. For example, we can add a data type `Restaurant`, teach it to calculate its average rating, and add that to its instruction set. Ruby programmers very often share these new classes with one another, making the language ever more powerful — Rails itself is largely just a collection of these new nouns and verbs related to web applications!

#### Ruby's Primary Syntax: `object.method`

So, in terms of **data** and **instructions**, Ruby comes with a powerful set out-of-the-box *and* is infinitely extensible! That's good news. Here's even more good news: to access all of this power, the **primary syntax** is simple:

```ruby
"Hello".downcase
```

On the left side of the dot we have our data, or, formally, an **object**. A *thing*, or *noun*, as I think of it.

On the right side of the dot we have our instruction, or, formally, a **method**. An *action*, or *verb*, as I think of it.

In this case, we asked `"Hello"`, which is a `String`, to `downcase` itself, which it happily does.

What if we try asking the number `9` to downcase itself? Try it right now in `rails console`.

```ruby
9.downcase
```

Aha! `NoMethodError: undefined method 'downcase' for 9:Fixnum`. It looks scary, but one of your main objectives during this course is to **not panic** when you see an error message. Slow down, read it carefully, and see if you can make any sense of it at all. Over time, you will find that they are very helpful — and you will miss them when something is going wrong *silenty*.

In this case, it is saying: "Hey, dummy — you can't downcase 9, which is a number." Fair enough. (`Fixnum` means "integer", as opposed to `Float` which means "decimal number". Almost all programming languages use two distinct data types for those two things.)

At all times as you are writing Ruby, you should be thinking: **What class of object do I have?** **What methods can I call on this kind of object?**

Alright, so the **primary syntax** in Ruby is very simple — `object.method`. However, here's one small wrinkle: some methods require additional inputs. For example, there is a method called `gsub` which we can call on `String`s, which will substitute characters with other characters. Try it:

```ruby
"Hello".gsub("l", "z")
```

In order to do its job, the `gsub` method needs to know what character to substitute and what to replace it with. So we give it inputs, or **arguments**, which must come in parentheses immediately following the method (**no space after the method name**). If the method takes multiple arguments, as `gsub` does, then they are separated by commas.

In reality, `gsub` is more often used to do things like removing illegal characters from usernames before saving:

```ruby
"D+h+H".gsub("+", "")
```

(`""` is an empty string, so all `+`s get replaced with nothing.)

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

#### Variables

Remember, you can use your up and down arrows to scroll through your command history. But Ruby has a more important way to save data: we can create a box in memory to hold it and give that box a name, like so:

```ruby
s = "Hello"   # Create a box, label it `s`, and store "Hello" in it
s             # Retrieve the value in `s`
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
So, in addition to `object.method`, **the syntax you need to know like the back of your hand is**

```ruby
storage_box = the_final_value.resulting_from_this(expression).will_be_stored
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

Rubyists strive to choose descriptive variable names, no matter how long they are, so that the code reads almost like English -- avoid naming your variables `x`, `y`, and `z`. Use underscores to separate words in multiple word variable names.

## Conclusion

That's it for the primary syntax of Ruby!

```
storage_box = object.method(argument1, argument2, ...)
```

Now, we need to spend some time *expanding our vocabulary*. Let's start with [the most fundamental built-in classes that Ruby gives us](fundamental-classes.md).


[^1]: [MDN HTML element reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)

[^2]: [MDN CSS reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference)

[^3]: [Complex Selectors](http://learn.shayhowe.com/advanced-html-css/complex-selectors/)
