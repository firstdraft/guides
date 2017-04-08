mes# Loops in Ruby

## Conditionally doing something once

Consider the following program, which utilizes an `if` statement:

```ruby
a = []                    # Starting off an empty array

if a.length < 3           # This is true, since a is empty
  new_element = rand(100) # Generate a random number
  a.push(new_element)     # Push the new number into a
end

len = a.length
```

We start off with an empty array, `a`. If its length is less than `3` (this is true, since length is currently `0`), we push a new random number into it.

Once Ruby reaches the `end` statement paired with an `if`, it proceeds forward and continues to execute the rest of the code (whether the `if` condition was true or not).

At the end of the day, `a` has one element in it and `len` is `1`. 

## Conditionally doing something multiple times

Now, consider almost identical code, but with the `if` keyword swapped for another keyword — `while`:

```ruby
a = []

while a.length < 3
  new_element = rand(100)
  a.push(new_element)
end

len = a.length
```

`while` works almost exactly like `if` — it evaluates the expression next to it, and if it is true, it executes the code up until the `end`; if not, it ignores the code up until the `end`.

There is one key difference: if the condition is true, after we reach the `end`, the execution of the program **jumps back up to the `while` statement**. Then the condition is evaluated *again*. **If it is *still* true, then the code is executed again.** And then the execution of the program jumps back up to the `while` statement *again*. Etc.

So in this case,

 - the first time we reach the `end`, we jump back up to the `while`
 - evaluate `a.length < 3` again — still true, since `1 < 3`
 - so we push in another random number, and jump back up
 - `2 < 3`? Yep, so we do it again.
 - `3 < 3`? Nope, so now we skip down to the end and continue
 - and `len` ends up being `3`.

What we've seen here is our very first **loop**; code that is executed multiple times. It could be an arbitrary number of times, perhaps even an infinite number of times if we aren't careful.

## The importance of loops

Loops are absolutely essential to doing anything interesting with computing. If you want anything interactive, where the computer does something and then the user does something and then the computer reacts and then the user responds, etc, then you need a loop.

In fact, when you started up the `rails server`, you basically started a program that went into an infinite loop of listening for web requests so that it could send back responses (and that's why you have to force it to shut down with <kbd>Ctrl</kbd>+<kbd>C</kbd>).

But most importantly for us, as web developers: we spend 99% of our time **managing lists of things**. Lists of photos, likes, messages, events, reviews, users, tweets, whatever. These objects usually come to us in `Array`s, and we usually need to loop across (or "iterate over") the array and do some work with each element in the array (like draw some nice HTML around it). **So we need to get *really* good at iterating over arrays.**

## Easier loops in Ruby with `.each`

We could do all of our looping using the `while` statement, but Ruby gives us an easier way.

Since most of our looping as web developers is to do interesting things with elements in `Array`s, let me instead just show you a purpose-built `Array` method that we're going to use 1000 times a day: `.each`.

Let's suppose that I have an array of numbers. For some reason, let's suppose that I want to square each number in the array and then add up all the squares. I could do that work with the following code (which you should try out in `app/controllers/programs_controller.rb` and view the output at [http://localhost:3000/second](http://localhost:3000/second)):

```ruby
def second_program
  # Your code goes below.
 
  our_numbers = [4, 10, 6]        # Create an array of numbers
  squared_numbers = []            # Create an empty array
 
  our_numbers.each do |num|       # For each element in numbers, (refer to it as "num")
    square = num * num            # Square the number
    squared_numbers.push(square)  # Push it into the squared_numbers array
  end
  
  @your_output = squared_numbers.sum  # Sum the squares
   
  render("programs/second_program.html.erb")
end
```

Here's how `.each` works:

 - When we have an array and we need to do some work with every element in it, we use `.each`.
 - We put the `do` keyword next to it.
 - The `do` keyword has a matching `end` keyword, and the code to be repeated goes between them. (The whole thing from `do` through `end` is known as a "block".) I just type the matching `end` as soon as I type the `do` so that I don't forget it, just the same as when I type an opening tag in HTML.
 - After the `do` keyword, we put vertical bars known as "pipes" — `| |`. Within the pipes, **we choose a name that we want to use to refer to each element in the list as we are looping through it**. In this case, I chose "`num`". (This is known as a "block variable".)
 - Within the `do` and `end` block, I used the variable `num` while writing the code I want executed for each element in the list.
 - Voilà! Now we don't have to worry counting the length of the list, keeping a counter to keep track of where we are, indexing in to the list, etc; `.each` takes care of all of that.
 
So, while `while` is neat to know about, the most important looping method that you need to understand right now is `.each`.

The hardest part, I think, is getting your head around the block variable `|num|`. It takes some practice. Try to remember that it's just a name that we make up for use within the `do` and `end` block to refer to each element in the array as the loop is being executed. I could have called it `zebra` if I wanted to, and behind the scenes, Ruby would have assigned each element in the list to the variable `zebra` as we got to its turn.

Soon, you'll be embedding Ruby loops in your view templates to create dynamic, data-driven pages with code that looks something like this:

```erb
<% timeline_photos.each do |the_photo| %>
  <div class="card">
    <img src="<%= the_photo.image_source %>">
    
    <p>
      <%= the_photo.caption %>
    </p>
  </div>
<% end %>
```

So it's important to clear up fuzziness now about the pure Ruby parts of it.

## Challenge

If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Can you find the sum of all the multiples of 3 or 5 below 1000?

Try writing a program in `app/controllers/programs_controller.rb` within:

```ruby
def third_program
  numbers = (1..999).to_a

  # Your code goes below.

  @your_output = "Replace this string with your output"

  render("programs/third_program.html.erb")
end
```

and view your output at [http://localhost:3000/third](http://localhost:3000/third). I've provided a variable for you, `numbers`, which has an array in it containing the first 999 natural numbers.

(Credit for this challenge goes to [Project Euler](https://projecteuler.net). This is the first in a series of puzzles that they provide. You can check your answer by signing up for an account there and submitting it, and find lots more puzzles to practice your Ruby on!)


