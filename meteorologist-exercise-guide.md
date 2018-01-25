# Meteorologist

## There is a Getting Started video on Canvas. Go watch that first.

## Introduction

In this project, you will practice working with Arrays and Hashes by pulling data from external services like Google Maps. You will build an application that, given a street address, tells the user the weather forecast.

### [Here is a functional version of the app -- this is your target.](https://meteorologist.herokuapp.com/)

In order to achieve this, our first task will be to exchange a **street address** for a **latitude/longitude pair** using Google's Geocoding API.

We will send a location in a remarkably flexible, "English-y" format, the kind of thing we are allowed to type into a Google Maps search (e.g., "the corner of 58th and Woodlawn"), and the Geocoding API will respond with an exact latitude and longitude (along with other things) in JSON format.

### Getting Started

Any time you are trying to develop a proof of concept of an app that needs external API data, the first step is researching the API and finding out if the information you need is available.

For us, that translates to: is there a URL that I can paste into my browser's address bar that will give back JSON (JavaScript Object Notation) that has the data I need? If so, we're good; Ruby and Rails makes the rest easy.

First, let's install a Chrome Extension called JSONView that makes working with JSON easier:

https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc?hl=en

This will indent the JSON nicely and allow you to fold and unfold nested elements.

### Find an example

Now, we have to research the API and find the correct URL to paste into our address bar to get back the JSON that we want. Usually, we have to start at the API Documentation. For the Geocoding API, the full docs are here:

https://developers.google.com/maps/documentation/geocoding/

but, as usual with technical documentation, it's best once you skim the intro to head straight for the examples:

https://developers.google.com/maps/documentation/geocoding/start#geocoding-request-and-response-latitudelongitude-lookup

The first example they give is

[https://maps.googleapis.com/maps/api/geocode/json?address=1600+Amphitheatre+Parkway,+Mountain+View,+CA](https://maps.googleapis.com/maps/api/geocode/json?address=1600+Amphitheatre+Parkway,+Mountain+View,+CA)

(I have removed the part about the API key from the end of the URL; we don't need one, for now.) Paste that URL into a Chrome tab; you should see something like this:

![](/assets/mapsjson.png)

Try folding away the `address_components` section to make the value of the `geometry` key stand out, since that is where our target information lives:

![](/assets/folded-mapsjson.png)

Notice the `lat` and `lng` keys within the `location` hash. Notice that JSON uses curly braces for Hashes and square brackets for Arrays just like Ruby does.

Alright, now that we have the data we need showing up in the browser window, what's next? First of all, we should be sure that we can customize this example request to get data that we care about. So how would we get the coordinates of "5807 S Woodlawn Ave" instead of Google's HQ? Give it a try.

---

No really, try it yourself!

---

You'll have to modify the example URL somehow.

---

It turns out we need to replace the part of the URL after the `?address=` with the address we want geocoded:

![](/assets/Screen Shot 2018-01-25 at 3.46.15 PM.png)

(Spaces are not legal in URLs, so we have to **encode** them. One way to encode them can be seen in Google's example, with `+`s. If you tried typing the address with spaces in it, you'll have noticed that Google encodes spaces automatically with `%20%`.)

### Ruby

Great! Now we know the exact data we want is available through the API. Now, how do we get it into our application? Fortunately, Ruby comes with some powerful built-in functionality that will help us with this. First, we need Ruby to read the URL that has the JSON we want, just like Chrome did. Chrome has an address bar we can paste the URL in to; how can we tell Ruby to go open a page on the Internet?

> If you haven't already, clone the project, `cd` into it, `bin/setup`, and then fire up a `rails console` session.

Let's use Ruby's `open()` method to read Google's page. The `open()` method takes one `String` argument, which should contain the URL of the page you want to open. I'm going to copy-paste the URL into `"  "` and store it in a variable `url` to make it easier to work with:

```ruby
pry(main)> url = "https://maps.googleapis.com/maps/api/geocode/json?address=5807+S+Woodlawn+Ave"
```

Now let's `open` that URL and `read` the body of it:

```ruby
open(url).read
```

You should see something like this:

![](/assets/open-url-read.jpg)

> **Note:** To scroll through long output in `rails console`, you can use <kbd>return</kbd> to scroll one line at a time, <kbd>Space</kbd> to scroll one page at a time, or <kbd>Q</kbd> to just get back to the prompt to enter a new Ruby expression.


What just happened? We `open`ed the page at the location in `url`, and the return value was the HTTP response. The HTTP response is actually a complicated object, with headers and status codes and other things we haven't talked about yet.

All we really want is the body of the response, the stuff that shows up in the browser window, so we used the `.read` method to pull that out. However, we just dropped that string on the ground; let's instead store the result in a variable called `raw_data`:

```ruby
raw_data = open(url).read
```

Alright! We just used Ruby to open up a connection over the Internet to Google's servers, placed a request for them to translate our address into a latitude and longitude, received a response, and stored it in a Ruby variable! That's a big deal, folks. However, the response is hideous. How in the world are we going to pull out the latitude and longitude values from that thing?

We could explore the [String][1] class documentation and find some methods that might help us scan through `raw_data` for `"lat"`, perhaps. But then what? We could probably figure it out, but there's a much better way.

Fortunately, Ruby provides a class called `JSON`, similar to the `CSV` class, which makes parsing a string that has data in JSON format a snap:

```ruby
parsed_data = JSON.parse(raw_data)                                                           
```

and you should see

```ruby
=> {"results"=>
  [{"address_components"=>
     [{"long_name"=>"Chicago Booth Harper Center",
       "short_name"=>"Chicago Booth Harper Center",
       "types"=>["premise"]},
      {"long_name"=>"5807", "short_name"=>"5807", "types"=>["street_number"]},
      {"long_name"=>"South Woodlawn Avenue", "short_name"=>"S Woodlawn Ave", "types"=>["route"]},
      {"long_name"=>"South Side", "short_name"=>"South Side", "types"=>["neighborhood", "political"]},
      {"long_name"=>"Chicago", "short_name"=>"Chicago", "types"=>["locality", "political"]},
      {"long_name"=>"Cook County",
       "short_name"=>"Cook County",
       "types"=>["administrative_area_level_2", "political"]},
      {"long_name"=>"Illinois", "short_name"=>"IL", "types"=>["administrative_area_level_1", "political"]},
      {"long_name"=>"United States", "short_name"=>"US", "types"=>["country", "political"]},
      {"long_name"=>"60637", "short_name"=>"60637", "types"=>["postal_code"]},
      {"long_name"=>"1610", "short_name"=>"1610", "types"=>["postal_code_suffix"]}],
    "formatted_address"=>"Chicago Booth Harper Center, 5807 S Woodlawn Ave, Chicago, IL 60637, USA",
    "geometry"=>
     {"bounds"=>
       {"northeast"=>{"lat"=>41.789511, "lng"=>-87.5949885},
        "southwest"=>{"lat"=>41.7883316, "lng"=>-87.5961513}},
      "location"=>{"lat"=>41.7891369, "lng"=>-87.5954551},
      "location_type"=>"ROOFTOP",
      "viewport"=>
       {"northeast"=>{"lat"=>41.79027028029149, "lng"=>-87.59422091970849},
        "southwest"=>{"lat"=>41.7875723197085, "lng"=>-87.59691888029151}}},
    "place_id"=>"ChIJkb9VkxYpDogRSmVtpZC9s6s",
    "types"=>["premise"]}],
 "status"=>"OK"}
```

Look! Hash rockets! We've converted a cumbersome string into a beautiful, friendly Ruby Hash. Now, if I want to get down to the latitude and longitude, how would I do it? Well, remember, we already got a hint back when we first looked at the data in Chrome: it has something to do with the `geometry` key. We can remind ourselves what keys are in the hash:

```ruby
parsed_data.keys
=> ["results", "status"]
```

The data we want is probably inside the key "results". So lets step in one level deep and see what we have:

```ruby
parsed_data.fetch("results").class
=> Array
```

Let's go one level deeper by getting the first element and seeing what _it_ is:

> **Note:** As you explore, don't forget that you can use your UP ARROW to scroll through your command line history. You don't always have to re-type the same thing over and over!

```ruby
f = parsed_data.fetch("results").at(0)
f.class
=> Hash
```

Another hash — let's see what keys it has:

```ruby
f.keys
=> ["address_components", "formatted_address", "geometry", "place_id", "types"]
```

Alright, so we now have a Hash in `f` that has a key called `"geometry"`, which, as we learned from our initial research above, is what contains our target. Let's keep going:

```ruby
f.fetch("geometry")
=> {"bounds"=>
  {"northeast"=>{"lat"=>41.789511, "lng"=>-87.5949885},
   "southwest"=>{"lat"=>41.7883316, "lng"=>-87.5961513}},
 "location"=>{"lat"=>41.7891369, "lng"=>-87.5954551},
 "location_type"=>"ROOFTOP",
 "viewport"=>
  {"northeast"=>{"lat"=>41.79027028029149, "lng"=>-87.59422091970849},
   "southwest"=>{"lat"=>41.7875723197085, "lng"=>-87.59691888029151}}}
```

Closer!

```ruby
f.fetch("geometry").fetch("location")
=> {"lat"=>41.7891369, "lng"=>-87.5954551}
```

Almost there!

```ruby
f.fetch("geometry").fetch("location").fetch("lat")
=> 41.7891369
f.fetch("geometry").fetch("location").fetch("lng")
=> -87.5954551
```

Woo! We made it all the way down to what we want. Phew! Now, I did it in a bunch of tiny steps, which might have made it seem complicated, but we could also have just done it in one step:

```ruby
parsed_data.fetch("results").at(0).fetch("geometry").fetch("location").fetch("lng")
=> -87.5954551
```

I prefer working in small steps and peeling one layer off at a time while I am exploring. But, once I know what I need, there's also a method called `dig` that can help us drill down into nested Hash/Array structures like this a bit more concisely:

```ruby
parsed_data.dig("results", 0, "geometry", "location", "lng")
=> -87.5954551
```

So, the entire program boils down to just three lines!

```ruby
parsed_data = JSON.parse(open(url).read)
latitude = parsed_data.dig("results", 0, "geometry", "location", "lat")
longitude = parsed_data.dig("results", 0, "geometry", "location", "lng")
```

And now I can do whatever interesting things with `latitude` and `longitude` that I need.

Now that we've explored in the console, it's time to take these three lines (or something like them, anyway) and write some permanent programs...

## Part 1: Street &rarr; Coords

Now that we've seen how to retrieve information from a URL using Ruby, let's plug it in to a real application.

I have started you off with three forms:

 - [Street &rarr; Coords](http://localhost:3000/street_to_coords/new)
 - [Coords &rarr; Weather](http://localhost:3000/coords_to_weather/new)
 - [Street &rarr; Weather](http://localhost:3000/street_to_weather/new)

And three actions which process these form inputs and render results:

 - `app/controllers/geocoding_controller.rb`
 - `app/controllers/forecast_controller.rb`
 - `app/controllers/meteorologist_controller.rb`

We'll be working on [Street &rarr; Coords](http://localhost:3000/street_to_coords/new) first.


Open the file `app/controllers/geocoding_controller.rb`. Your job is to write some code in the `street_to_coords` method, where indicated, and put the correct value in the `@latitude` and `@longitude` variables.

If I type in `5807 S Woodlawn Ave` at the [Street &rarr; Coords form](http://localhost:3000/street_to_coords/new), I should see something like

<blockquote>
<dl>
  <dt>Street Address</dt>
  <dd>5807 S Woodlawn Ave</dd>

  <dt>Latitude</dt>
  <dd>41.7896234</dd>

  <dt>Longitude</dt>
  <dd>-87.5964137</dd>
</dl>
</blockquote>


## Part 2: Coords &rarr; Weather

Next, in `app/controllers/forecast_controller.rb`, you will do something similar; but instead of using Google's Geocoding API, you will use The Forecast API. We will exchange a latitude/longitude pair for weather information. Forecast is an amazing API that gives you minute-by-minute meteorological information.

They released an iOS app, Dark Sky, to demonstrate the power of their API, and it instantly became a smash hit. The API is not entirely free, but we get 1,000 calls per day to play around with.

Step 1 when working with any API is research. What is the URL of the page that has the data we want, preferably in JSON format?

Let's head over to [Forecast's API documentation][2]. First, we must register as developers:

<img src='http://ask.initialversion.com/uploads/default/80/ae376d887782c8bb.png' width="690" height="412">

You need not provide a real email address, if you don't want to. Once you register, you will be given an example link with your own personal API key inserted in a variable path segment:

<img src='http://ask.initialversion.com/uploads/default/81/80aa59c81d8cc53d.png' width="690" height="412">

#### Find an example

Click the example link and check out the data they provide. Scroll up and down and get a feel for it:

<img src='http://ask.initialversion.com/uploads/default/82/6a23cb4cd7f20112.png' width="690" height="412">

It's pretty amazingly detailed data; it tells us current conditions, along with minute-by-minute conditions for the next hour, hour-by-hour conditions for the next day or so, etc.

But first, can we customize the example to get data relevant to us? Plug in some coordinates that you fetched in `street_to_coords` and try it out.

Your job is to write some code in the `coords_to_weather` method, where indicated, and put the correct value in the instance variables at the end.

If I type in `41.78` and `-87.59` at the [Coords &rarr; Weather form](http://localhost:3000/coords_to_weather/new) , I should see something like

<blockquote>
<dl>
  <dt>Latitude</dt>
  <dd>41.78</dd>

  <dt>Longitude</dt>
  <dd>-87.59</dd>

  <dt>Current Temperature</dt>
  <dd>73.35</dd>

  <dt>Current Summary</dt>
  <dd>Clear</dd>

  <dt>Outlook for next sixty minutes</dt>
  <dd>Clear for the hour.</dd>

  <dt>Outlook for next several hours</dt>
  <dd>Partly cloudy tomorrow morning.</dd>

  <dt>Outlook for next several days</dt>
  <dd>No precipitation throughout the week, with temperatures falling to 62°F on Tuesday.</dd>
</dl>
</blockquote>

**Note: Forecast does not have data for every lat/lng combination; some geographies will return `nil`s.** If you run into issues, you can try Ruby 2.3's handy new `Hash#dig` method:

```ruby
parsed_results.dig("minutely", "summary")
```

rather than

```ruby
parsed_results["minutely"]["summary"]
```

The latter, if `parsed_results["minutely"]` is `nil`, will throw an error complaining that you can't do `nil["summary"]`. The former will handle the issue more gracefully. [Read more in this StackOverflow thread.](https://stackoverflow.com/questions/34346653/how-do-i-use-arraydig-and-hashdig-introduced-in-ruby-2-3)

## Part 3: Address to Weather

Finally, pull it all together in `app/controllers/meteorologist_controller.rb`. Use both the Google Geocoding API and the Forecast API so that if I type in `5807 S Woodlawn Ave` at the [Street &rarr; Weather form](http://localhost:3000/street_to_weather/new), I should see something like

<blockquote>
<p>Here's the outlook for 5807 S Woodlawn Ave:</p>

<dl>
  <dt>Current Temperature</dt>
  <dd>73.35</dd>

  <dt>Current Summary</dt>
  <dd>Clear</dd>

  <dt>Outlook for next sixty minutes</dt>
  <dd>Clear for the hour.</dd>

  <dt>Outlook for next several hours</dt>
  <dd>Partly cloudy tomorrow morning.</dd>

  <dt>Outlook for next several days</dt>
  <dd>No precipitation throughout the week, with temperatures falling to 62°F on Tuesday.</dd>
</dl>
</blockquote>

## Submission

Remember to make lots of commits as you work. Use the [Continuous Integration](https://guides.firstdraft.com/continuous-integration.html) workflow as usual to open a Pull Request to submit your work.

 **And ask lots of questions!** Really. Ask early and often.

Good luck!

## Optional Extra Exercises, for fun

### Programmable Web (Easier)

Browse [Programmable Web's API Directory](http://www.programmableweb.com/category/all/apis?order=field_popularity) and get inspired!

### Bootstrap (Easier)

`<link>` to Bootstrap or a Bootswatch in the `<head>` of your pages (located in `app/views/layouts/application.html.erb`), and make things look prettier.

You can take [Omnicalc](http://omnicalc-target.herokuapp.com/) as inspiration, or create something entirely new.

### Future Forecast (Harder)

The Forecast API can take a third parameter in the URL, time:

https://developer.forecast.io/docs/v2#time_call

Add a feature that shows summaries for the next 14 days.

### Google Map (Harder)

Embed a Google map in the view, centered on the provided address. Refer to the docs:

https://developers.google.com/maps/documentation/javascript/examples/map-simple

The key concept is, just like with Bootstrap, to first paste in the example markup and see if it works.

Then, replace whichever part of the static markup you want to with embedded Ruby tags that contain your dynamic values.


  [1]: http://www.ruby-doc.org/core-2.2.1/String.html
  [2]: https://developer.forecast.io/
