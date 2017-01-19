# Loops in Ruby

Consider the `if` statement:

```ruby
a = []

if a.length < 3
  new_element = rand(100)
  a.push(new_element)
end

len = a.length
```

We start off with an empty array, `a`. If its length is less than `3` (this is true, since length is currently `0`), we push a new random number into it.

Once Ruby reaches the `end` statement paired with an `if`, it proceeds forward and continues to execute the rest of the code (whether the `if` condition was true or not). So `len` is now `1`. 

Now, consider almost identical code, but with the `if` keyword swapped for another keyword -- `while`:

```ruby
a = []

while a.length < 3
  new_element = rand(100)
  a.push(new_element)
end

len = a.length
```

`while` works exactly like `if` -- it evaluates the expression next to it, and if it is true, it executes the code up until the `end`; if not, it ignores the code up until the `end`.

There is one key difference: if the condition is true, after we reach the `end`, the execution **jumps back up to the `while` statement**. Then the condition is evaluated *again*. **If it is *still* true, then the code is executed again.** Etc.

So in this case,

 - the first time we reach the `end`, we jump back up to the `while`
 - evaluate `a.length < 3` again -- still true, since `1 < 3`
 - so we push in another random number, and jump back up
 - `2 < 3`? Yep, so we do it again.
 - `3 < 3`? Nope, so now we skip down to the end and continue
 - and `len` ends up being `3`.

What we've seen here is our very first **loop**; code that is executed multiple times. It could be an arbitrary number of times, perhaps even an infinite number of times if we aren't careful.

Loops are absolutely essential to doing anything interesting with computing. If you want anything interactive, where the computer does something and then the user does something and then the computer reacts and then the user responds, etc, then you need a loop.

In fact, when you started up the `rails server`, you basically started a program that went into an infinite loop of listening for web requests so that it could send back responses (and that's why you have to force it to shut down with <kbd>Ctrl</kbd>+<kbd>C</kbd>).

But most importantly for us, as web developers: we spend 99% of our time **managing lists of things**. Lists of photos, likes, messages, events, reviews, users, tweets, whatever. These objects usually come to us in `Array`s, and we usually need to loop across (or iterate over) the array and do some work with each element in the array (like draw some nice HTML around it). **So we need to get *really* good at looping over arrays.**

We could do this using the `while` statement, but let me just show you a purpose-built `Array` method that we're going to use 1000 times a day instead: `.each`:

```ruby
 numbers = [4, 10, 6]            # Create an array of numbers
 squared_numbers = []            # Create an empty array
 
 numbers.each do |num|           # For each element in numbers,
                                 #   (referring to it as "num")   
   squared_numbers.push(num**2)  # Square it and push into
                                 #   squared_numbers
 end
 
 squared_numbers.sum             # Sum the squares
```

Here's how `.each` works:

 - We call it on an array that we want to loop across.
 - We put the `do` keyword next to it.
 - The `do` keyword has a matching `end` keyword, and the code to be repeated goes between them. (The whole thing from `do` through `end` is known as a "block".)
 - After the `do` keyword, we put vertical bars known as "pipes" -- `| |`. Within those, we choose a name that **we want to refer to each element in the list as we are looping through it**. In this case, I chose "`num`". (This is known as a "block variable".)
 - Inside the `do`/`end`, I used the variable `num` to write the code I want executed for each element in the list.
 - Voilà! Now we don't have to worry counting the length of the list, keeping a counter to keep track of where we are, indexing in to the list, etc; `.each` takes care of all of that.
 
So, while `while` is neat to know about, the most important looping method that you need to understand right now is `.each`.

The block variable `|num|` part takes a bit to get your head around -- it's just a name we make up for use within the `do`/`end` to talk about each element in the array as the loop is being executed. I could have called it `zebra` if I wanted to.

Soon, you'll be putting both HTML and Ruby together to create beautiful pages with code that looks something like this:

```erb
<% timeline_photos.each do |photo| %>
  <div class="photo">
    <img src="<%= photo.image_source %>">
    
    <p class="caption"><%= photo.caption %></p>
  </div>
<% end %>
```

So it's important to clear up fuzziness now about the pure Ruby parts of it.

