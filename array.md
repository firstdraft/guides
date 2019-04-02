# `Array`

Finally, we have a very important class: `Array`. Most of what we do as web
developers is manage _lists of things_. Lists of photos, likes, followers,
reviews, listings, messages, whatever.

The first structure we're going to learn to help us manage lists is `Array`.
Here's how they work:

```ruby
a = [8, 3, 1, 19, 23, 3]
```

-   The way we create `String`s by wrapping the string of characters in
    double-quotes, we create `Array`s by wrapping the list of elements in square
    brackets.
-   Seperate elements in the list with commas.

## Methods

### `count`
Counts all elements in the list and can count the occurrences of an argument.
### `reverse`

### `sort`

### `shuffle`

### `sample`

### `min`

### `max`

### `sum`

### `first`

### `last`

### `second`

### `at`
Accesses an element in the array at the position given as an argument.
Positioning in an array starts at 0. Given an array of `[21, 7, 99, 34, 13]`,
`21` is in position 0, `7` is in position 1, `99` is in position 2, and so on...

### `[]`
This is a shorthand syntax for `at()`.
### `push`

### `count`

## To Learn More

That's a fun selection of some common methods, but obviously there are a lot
more. To learn more, usually my MO is: start building something, run into a
situation where I need a new tool, like: "How do I find what spot in an array a
particular element is at?"

Then, you should, in order:

-   Post a question on Piazza. You are brand new to programming and the answers
    that you will find on the internet will oftentimes be advanced or just flat
    out wrong, and you won't yet be able to tell the difference easily. So for
    now, lean on us and each other.
-   Check the Ruby Docs for whichever class you are wondering about. In this
    case, the [Array docs](https://ruby-doc.org/core-2.2.0/Array.html). Scan the
    method list on the left until you see something that looks kinda right, and
    then check out the examples. (In this case,
    [#index](https://ruby-doc.org/core-2.2.0/Array.html#method-i-index) sounds
    about right.)
-   Google it and hope to find a helpful blog post or Stack Overflow answer.
-   Trial and error! The life of a developer.

## Next Up

Alright! It's been fun playing around with Ruby in a console, but how
would we actually builds some real, [permanent programs](permanent-programs.md)
that we can share with our friends? That's what we'll see next.
