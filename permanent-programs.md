# Permanent Programs

Now that you're comfortable writing some Ruby, let's learn how to write some real programs!

It's not very much fun typing commands over and over into `rails console`, only to have them forever lost if you close Terminal. So let's write them down permanently into a source code file, just like you did with your HTML.

Open the folder of code that you downloaded at the beginning of this project in Atom. In the drawer on the left, locate the file `app/controllers/programs_controller.rb`.

In that file, you should see some code that looks like this:

```ruby
class ProgramsController < ApplicationController
  def home
    # Your code goes here.

    @your_output = "Replace this string with your output"

    render("programs/home.html.erb")
  end
end
```

For now, ignore most of it; we'll dig into what every character in there means, eventually. But right now, just change the string `"Replace this string with your output"` to any Ruby expression that you want. It could be anything that you just learned -- `7*6`, `rand(100)`, `"hElLO".swapcase` -- and then refresh this page and check out the box below -- it should contain your output:

```
<div class="well"><%= @your_output %></div>
```

Voilà! You've just written your first dynamically generated webpage! In Chrome, View Source on the page and you'll see that it had no idea that you wrote the page using Ruby rather than typing it out by hand. It just drew the source code as usual. Congratulations!

Even better, you can type a whole succession of expressions on the lines above to build up more complicated programs. Try something like:

```ruby
class ProgramsController < ApplicationController
  def permanent_programs
    # Your code goes here.
    
    my_birthday = Time.parse("July 1st, 2000")
    today = Time.now
    seconds_since_i_was_born = today - my_birthday
    
    @your_output = seconds_since_i_was_born
    
    render("programs/permanent_programs.html.erb")
  end
end
```

or any other program that you'd like! Just assign the final value that you'd like to appear on this page to the special variable `@your_output`. Now that we know how to write permanent, multiline programs, there's one more thing we need to see before we can write some fun projects: [conditionals](conditionals.md).