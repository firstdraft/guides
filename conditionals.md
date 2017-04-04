# Conditionals

Previously, we mentioned that Ruby allows us to compare values, and returns `true` or `false`:

```ruby
1 < 2          # "1 is less than 2"
2 < 1          # "2 is less than 1"
24*365 > 10000 # There are more than 10,000 hours in a year
1 == 1         # "1 is equivalent to 1"
1 == 2         # "1 is equivalent to 2"
1 != 1         # "1 is NOT equivalent to 1"
1 != 2         # "1 is NOT equivalent to 2"
```

This becomes useful in conjunction with the `if` statement, which allows us to do things _conditionally_ in our programs, rather than doing them on every run.

Let's see how this works. Locate the file called `app/controllers/programs_controller.rb` and let's write some code where it says:

```ruby
def home
  # Your code goes here

  @your_output = "Replace this string with your output"

  render("programs/home.html.erb")
end
```

First, try this:

```ruby
def home
  if 1 < 2
    @your_output = "duh"
  end

  render("programs/home.html.erb")
end
```

Now switch the `1 < 2` to `2 < 1` and refresh this page.

Ok, here's the deal with `if`:

 - It **must** have a matching `end`, so just type it before you type anything else and forget it.
 - Code that comes between the `if` and `end` will only be executed if the expression next to the `if` evaluates to `true`.
 - If the expression is `false`, then the code will simply be ignored.

You can also have _multi-branch_ `if` statements:

```ruby
def home
  the_number = rand(100)

  if the_number < 25
    @your_output = "It's going to be your lucky day today"
  elsif the_number > 75
    @your_output = "Don't leave home today"
  else
    @your_output = "It'll be an okay day today"
  end

  render("programs/home.html.erb")
end
```

 - Note that there's no space in `elsif`.
 - The conditions are checked in top-down priority, so even if more than one is true, whichever one is first has its branch executed; the rest are ignored.
 -  If none are true, the final `else` fallback branch is executed; but you don't have to have one if you don't want one.

Inside a branch of an `if` statement, you can have as many lines of code as you want -- and you can even have whole other multi-branch if statements, if that's what you need.

Finally, another handy thing to have in your toolbelt are the **logical operators** `&&` and `||`. These allow you to combine comparisons; try these:

```
1 < 2 && 2 < 3 # Is 1 less than 2 AND 2 less than 3? Duh
1 < 2 && 3 < 2 # Is 1 less than 2 AND 3 less than 2? I guess not
2 < 1 && 3 < 2 # Is 2 less than 1 AND 3 less than 2? Duh
1 < 2 || 2 < 3 # Is 1 less than 2 OR 2 less than 3? Yep
1 < 2 || 3 < 2 # Is 1 less than 2 OR 3 less than 2? I guess so
2 < 1 || 3 < 2 # Is 2 less than 1 OR 3 less than 2? Duh
```

Basically, `&&` is stricter than `||`; both comparisons have to be true in order for the whole statement to be true when combined with `&&`; either one being true is sufficient for `||`.

Challenge: Can you write a program that randomly chooses between "rock", "paper", and "scissors", and displays it on the page on each refresh?

## Next Up

As you might be starting to notice, computers just do very simple things, but they do them really fast. And one of the most useful things to do have computers do quickly for us is process big lists of things. For that, we need to learn about [Loops in Ruby](loops-in-ruby.md).