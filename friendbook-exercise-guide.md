# Friendbook Exercise Guide

In this project, we'll create our very first HTML page; a profile of ourselves. In the end, we'll work our way up to something that looks like [this target](http://appdevspring16.github.io/friendbook/raghu-b.html).

## Structure with HTML

### Raw Content

We'll start by getting the raw content into the page, and ignore styling for now. Our first target is something that looks like [this target](http://appdevspring16.github.io/friendbook/intermediate.html).

 1. Create your own page called `[first name]-[last-initial].html` (for example, I called mine `raghu-b.html`).
 1. Type in your own content:
   - Your name
   - Where you're from
   - Some of your app ideas
   - Some of your prior experience (jobs, education), and your LinkedIn URL
   - A favorite nearby haunt (coffee shop or restaurant or pub)

### Add Semantic Markup

 Next, let's tag our content to let the browser know what each thing is. Useful HTML elements include:

 - Headings: `<h1>`, `<h2>`, ... , `<h6>`
 - Paragraph: `<p>`
 - Unordered list: `<ul>`
 - Ordered list: `<ol>`
 - List item: `<li>`
 - Link: `<a href="http://www.addressofsomepage.com/whatever">`

### Add Images

Let's add some images to the page:

- A profile photo (you can grab a fake one from [UIFaces](http://uifaces.com/authorized))
- A cover photo (you can grab a stock one from [Stock Up](http://www.sitebuilderreport.com/stock-up))
- A few of your photos (you can grab fakes ones from [Stock Up](http://www.sitebuilderreport.com/stock-up))

After you download your images, name them similarly to what you called your HTML file:

 - `[first name]-[last-initial]-profile.jpg`
 - `[first name]-[last-initial]-cover.png`
 - `[first name]-[last-initial]-1.png`
 - `[first name]-[last-initial]-2.jpg`
 - `[first name]-[last-initial]-3.png`
 - `[first name]-[last-initial]-4.jpg`

Then, add them into your document using the `img` tag:

```html
  /* An image located in the same folder as this document */
  <img src="whatever.jpg">

  /* An image located somewhere on the Internet */
  <img src="http://somewhere.com/whatever.jpg">
```

### Tables

Let's put your experience data into a table. In HTML, the `<table>` element is used to represent two dimensional data. A simple table looks like this:

    <table>
      <tr>
        <th>First</th>
        <th>Last</th>
      </tr>
      <tr>
        <td>John</td>
        <td>Doe</td>
      </tr>
      <tr>
        <td>Jane</td>
        <td>Doe</td>
      </tr>
    </table>

which would produce this:

<table>
  <tr>
    <th>First</th>
    <th>Last</th>
  </tr>
  <tr>
    <td>John</td>
    <td>Doe</td>
  </tr>
  <tr>
    <td>Jane</td>
    <td>Doe</td>
  </tr>
</table>

The things to keep in mind about tables are:

 - Every piece of data must reside within a cell, a `<td>` element (or maybe a `<th>` element if it's a heading).
 - Every `<td>` or `<th>` element must reside within a row, a `<tr>` element.
 - Every `<tr>` must have the same number of cells, or things get out of whack.

Despite this last rule, you can, however, "merge" cells using the `colspan` attribute:

    <table>
      <tr>
        <th colspan="2">People</th>
      </tr>
      <tr>
        <td>John</td>
        <td>Doe</td>
      </tr>
      <tr>
        <td>Jane</td>
        <td>Doe</td>
      </tr>
    </table>

produces:

<table>
  <tr>
    <th colspan="2">People</th>
  </tr>
  <tr>
    <td>John</td>
    <td>Doe</td>
  </tr>
  <tr>
    <td>Jane</td>
    <td>Doe</td>
  </tr>
</table>

You can see that we've merged two cells in the first row together; the `colspan="2"` on the first cell ensures that we don't violate the "every `<tr>` must have the same number of cells" rule.

**Your task:** Try to create a "What I've Done" section similar to [the one you see here](http://appdevspring16.github.io/friendbook/intermediate.html).

### Embedding Objects

- Add a Google Map of your favorite nearby haunt
- Add a Vine that you like [(here are some examples to choose from)](https://vine.co/Zach.King?mode=list)
- Add a YouTube video that you like [(here are some examples to choose from)](https://www.youtube.com/watch?v=nCKkHqlx9dE)

## Styling with CSS

Now that we have our content showing up, and we've added some basic structure with HTML, it's time to customize the styling of the page.

The basic syntax of CSS looks like this:

```html
<h1 class="greeting">Hi there</h1>

<style>
  .greeting {
    font-size: 24px;
    color: darkgrey;
  }
</style>
```

The rest is just practice, and expanding our vocabulary of what CSS properties are available to us.

Below are some resources that might be helpful as we go along:

 - [Google Web Fonts](https://www.google.com/fonts)
 - Google Web Font showcases: [Beautiful Web Type](http://hellohappy.org/beautiful-web-type) and [Typographic Project](http://femmebot.github.io/google-type/)

 - Hero unit with cover image:

        .top-cover {
          background: url("cover.jpg") no-repeat center bottom;
          background-size: cover;
          height: 300px;
        }

 - [Material-Design](https://www.google.com/design/spec/material-design/introduction.html)-style box shadow:

        .some-thing {
          box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
          transition: all 0.2s ease-in-out;
        }

        .some-thing:hover {
          box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
        }

 - [HTML5 Element List](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)

 - An abbreviated list of other useful CSS properties and example values:

        /* Typography */

        color: orange;
        font-family: 'Playfair Display', serif;
        font-size: 18px;
        font-weight: bold;
        letter-spacing: 0.4em;
        line-height: 1.86;
        text-align: center;
        text-decoration: none;
        text-transform: uppercase;

        /* Box Model */

        border-color: rgb(240, 240, 240);
        border-style: solid;
        border-width: 5px;
        border: thick white solid;
        height: 200px;
        margin: auto;
        padding-bottom: 20px;
        padding-left: 20px;
        padding-right: 20px;
        padding: 20px;
        width: 100%;

        /* Table */

        border-spacing: 10px;
        vertical-align: top;

         /* Other */

        background-color: rgba(0, 0, 0, 0.5)
        box-shadow: 0 1px 3px rgba(0,0,0,0.12);
        list-style-type: square;