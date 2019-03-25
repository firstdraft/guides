# Dates Cheatsheet

In this guide, I'll show you how I prefer to handle dates.

We'll

 1. use a gem called Chronic to intelligently parse a wide variety of user input into valid Dates,
 2. I'll also show you a gem that helps create nice looking datepicker controls,
 3. look at some built-in Ruby/Rails methods that help us format dates and times nicely for our users to look at.

## Chronic

The Chronic gem will help handle parsing user input strings into valid Date objects before saving them into your date columns.

In your Gemfile, include

```ruby
gem "chronic"
```

and then `bundle install` and restart your `rails server`..

In your controller actions, wherever you are assiging a value to a `date` column, use the `Chronic.parse()` method:

```ruby
def create
  @event = Event.new
  @event.title = params.fetch("title")
  @event.start_time = Chronic.parse(params.fetch("start_time"))
  @event.save
end
```

That's it! Your user can now supply inputs like

 - thursday
 - november
 - summer
 - friday 13:00
 - mon 2:35
 - 4pm
 - 10 to 8
 - 10 past 2
 - half past 2
 - 6 in the morning
 - and many more

Chronic will do its best to figure it out. At a minimum, Chronic solves the issue of Ruby using the international, DD/MM/YYYY, format by default. [See the official gem docs for more info.](https://github.com/mojombo/chronic)

## Bootstrap Datepicker

The `bootstrap4-datetime-picker-rails` gem will help create nice looking datepickers in your forms, so that users don't have to type in dates and times manually.

In your Gemfile, include

```ruby
gem "jquery-rails"
gem "momentjs-rails", ">= 2.9.0"
gem "bootstrap4-datetime-picker-rails"
```

and then `bundle install` and restart your `rails server`.

In `app/assets/javascripts/application.js`, add the lines

```js
//= require jquery
//= require jquery_ujs
//= require moment
//= require bootstrap-datetimepicker
//= require tempusdominus-bootstrap-4.js
```
In `app/assets/stylesheets/application.css`, add the line

```css
*= require bootstrap-datetimepicker
```

Now, in your forms, you can add inputs like this:

```html
<div class="form-group">
    <div class="input-group date" id="datetimepicker1" data-target-input="nearest">
        <input type="text" class="form-control datetimepicker-input" data-target="#datetimepicker1"/>
        <div class="input-group-append" data-target="#datetimepicker1" data-toggle="datetimepicker">
            <div class="input-group-text"><i class="fa fa-calendar"></i></div>
        </div>
    </div>
</div>
```

At the bottom of your view, or anywhere below the `<input id="datetimepicker1">`, include this JavaScript snippet:

```html
<script type="text/javascript">
    $(function () {
        $('#datetimepicker1').datetimepicker();
    });
</script>
```
**The crucial thing is for the `id=""` attribute of the `<input>` tag to match the CSS selector in the `$('')` function.**

You should now be able to click into the input and see a nicely styled datetimepicker.

### Pre-select a Date
To pre-select a date (for example, on an edit form), modify the JavaScript to look something like this:

```erb
<script>
  $(function () {
    $('#datetimepicker1').datetimepicker({
      defaultDate: "<%= @event.start_time.strftime("%m/%d/%y") %>"
    });
  });
</script>
```

where `@event.start_time` returns the date you want to be pre-selected.

LOTS more options on how to use it can be found in [the official docs](https://tempusdominus.github.io/bootstrap-4/).

## Formatting Dates and Times

### STRFTIME

Use the `.strftime` method on any Date or Time object:

```erb
<%= event.held_at.strftime('%B %e, %Y at %l:%M%P') %>
```

Use [the wonderful STRFTIME.net tool](http://strftime.net/) to help compose your formatting string.

### Time Ago In Words

Use the wonderful view helper method `time_ago_in_words()` to get the distance between the time and now in English:

```erb
<%= time_ago_in_words(event.created_at) %> ago
```

## Further reading:

 - [Dealing with timezones effectively in Rails](https://www.reinteractive.net/posts/168-dealing-with-timezones-effectively-in-rails)
