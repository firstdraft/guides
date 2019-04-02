# `String`
We've already met the `String` class a few times, but here are some handy
methods to try:
## Methods
### `+`
`String`s can be added together
### `*`
`String`s can be multiplied, but the order matters
### `upcase`

### `downcase`

### `swapcase`

### `reverse`

### `length`

### `chomp`

### `gsub`

### `to_i`
Sometimes you have a string that contains a number, usually input from a user,
and want to do math on it. `to_i` will attempt to convert a `String` object into
an `Integer` object.

### `strip`
`strip` removes all leading and trailing whitespace

### `gsub(/\s+/, "")`
This is an advanced technique that removes all whitespace
### `gsub(/[^a-z0-9\s]/i, "")`
This is an advanced technique that removes everything except alphanumerics and
whitespace
### `capitalize`

### `gsub(/[^a-z0-9\s]/i, "").strip`

### `capitalize`

### `titlecase`

### `split`
This produces an Array, which you can read about [here.](array.md)

### `split.count`
Arrays are lists, and can be counted.
### `.in?`

### `present?`

### `blank?`

## More
We spend a lot of time composing strings of output for our users, so let's see a
few more examples. Try this:

```ruby
message = "Your lucky number for today is " + rand(100) + "."
```

You'll see that Ruby gets confused, because we are trying to add an integer to a
string and it doesn't feel comfortable with that.

The solution is to tell the integer to convert itself to a string first:

```ruby
message = "Your lucky number for today is " + rand(100).to_s + "."
```

The above technique for composing strings, adding them together with `+`, is
called **string concatenation**.

There's another technique for composing strings that I personally find a bit
easier; it's called **string interpolation**. It goes like this:

```ruby
message = "Your lucky number for today is #{rand(100)}."
```

Basically, inside the string, you place `#{}` where you eventually want your
value to go. Inside the curly braces, you can write any Ruby expression without
worrying about whether it is a string or not. The expression will be evaluated,
converted to a string, and added to the string right in that spot. You can
interpolate as many expressions as you want into a single string. Pretty neat!

If you find interpolation confusing, feel free to just use concatenation.
