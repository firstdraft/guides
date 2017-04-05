# Permanent Programs

Now that you're comfortable writing some Ruby, let's learn how to write some real programs!

It's not very much fun typing commands over and over into `rails console`, only to have them forever lost if you close Terminal. So let's write them down permanently into a source code file, just like you did with your HTML.

First, navigate to [http://localhost:3000](http://localhost:3000) in Chrome. If you don't see anything there, then you need to start up your `rails server` in a new tab of Terminal. Refer to the Getting Started video. You should see "Replace this string with your output" if all goes well.

## Writing some source code

Next, open the folder of code that you downloaded in Atom. In the drawer on the left, locate the file `app/controllers/programs_controller.rb`.

In that file, you should see some code that looks like this at the top:

```ruby
class ProgramsController < ApplicationController
  def home
    # Your code goes here.

    @your_output = "Replace this string with your output"

    render("programs/home.html.erb")
  end
  
  # There's some other stuff below this; ignore for now
end
```

For now, ignore most of it; we'll dig into what every character in there means, eventually. But right now, just change the string `"Replace this string with your output"` to any Ruby expression that you want. It could be anything that you just learned — `7*6`, `rand(100)`, `"hElLO".swapcase` — and then refresh [http://localhost:3000](http://localhost:3000). It should contain your output!

Voilà! You've just written your first dynamically generated webpage! In Chrome, View Source on the page and you'll see that it had no idea that you wrote the page using Ruby rather than typing it out by hand. It just drew the source code as usual. Congratulations!

Even better, you can type a whole succession of expressions on the lines above to build up more complicated programs. Try something like:

```ruby
class ProgramsController < ApplicationController
  def home
    # Your code goes here.
    
    my_birthday = Time.parse("July 1st, 2000")
    today = Time.now
    seconds_since_i_was_born = today - my_birthday
    
    @your_output = seconds_since_i_was_born
    
    render("programs/home.html.erb")
  end
end
```

or any other program that you'd like! Just keep all of your code between `# Your code goes here` and `render("programs/home.html.erb")`, and assign the final value that you'd like to appear on the page to the special variable `@your_output`. (Variables whose names begin with the letter `@` are called **instance variables**, and are the ones we intend to display to our users. You can create and use them just like any other variables.)

## Customizing the output

If you want to, you can start to customize the output, too. Locate the file `app/views/programs/home.html.erb`, which should currently look something like this:

```erb
<div class="container">
  <div class="row">
    <div class="col-md-12">

      <div class="jumbotron">
        <h1>
          <%= @your_output %>
        </h1>
      </div>

    </div>
  </div>
</div>
```

This is known as your **view template**. We'll learn a lot more about these when we dig deeper in to Rails, but for now, just know that you can write any HTML and CSS in here that you want.

You should leave the special tag `<%= @your_output %>` alone, though; just move it around or wrap it within new HTML if you want to.

You could also create multiple instance variables back in `programs_controller.rb` and use them in your view template, too:

```ruby
class ProgramsController < ApplicationController
  def home
    # Your code goes here.
    
    my_birthday = Time.parse("July 1st, 2000")
    today = Time.now
    seconds_since_i_was_born = today - my_birthday
    
    @your_output = seconds_since_i_was_born

    first = "Raghu"
    last = "Betina"
    
    @first_then_last = first + " " + last
    
    @last_then_first = last + ", " + first
    
    render("programs/home.html.erb")
  end
end
```

Now you can embed them in your view template inside the special **embedded Ruby (ERB)** tag, `<%=  %>`:

```erb
<div class="container">
  <div class="row">
    <div class="col-md-12">

      <div class="jumbotron">
        <h1>
          <%= @first_then_last %>
          
          <small>
            a.k.a. <%= @last_then_first %>
          </small>
        </h1>
        
        <p>
          aged exactly <%= @your_output %> seconds
        </p>
      </div>

    </div>
  </div>
</div>
```

## Next up

Now that we know how to write permanent, multiline programs, there's one more thing we need to see before we can write some fun projects: [conditionals](conditionals.md).