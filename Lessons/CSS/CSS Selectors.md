CSS selectors allow developers to identify which elements certain CSS properties should be applied to. A selector defines some sort of pattern that will match against specific elements of an HTML document or template, and are [well-supported](http://quirksmode.org/css/selectors/) by all modern browsers. Tools like *jQuery* also borrow many of the rules from CSS selectors for their own selection tasks, i.e. `$('.items')`. 

## Tag, class, and ID selectors
Different elements almost always require different styles. Lists will be styled differently from headings, backgrounds will have a different color than fonts, and so on. When we define CSS "rules" (properties that should be applied to specific elements), we need to identify the items that they should be applied to in order to give the browser enough information to render the page the way we intend for users to see it. CSS selectors exist for this reason.

The most common ways to identify particular elements for styling are by tag, class, or ID. Each would be represented as follows in CSS:

```css
/* Tag selectors, which will apply to any <body> elements */
body {
   ... css declarations ...
}

/* Class selectors, which will apply to any element with <.. class='items'> */
.items {
   ... css declarations ...
}

/* ID selectors, which will apply to the single element with <.. id='heading'> */
#heading {
   ... css declarations ...
}
```

## Using multiple selectors
These rules can also be combined with each other to apply rules to more specific elements, i.e. distinguishing list items that are part of the site's navigation from list items that are part of a bulleted list in the body of a document. Selectors can be combined using *combinators* (symbols used to indicate a relationship between selectors) but even multi-part selectors are usually referred to as simply "selectors."

Furthermore, multiple combinators can be combined to create even more specific selectors. See the examples section below for more complex cases.

### Descendent combinator : `#navigation li`
Descendent combinators select elements that are nested beneath other specified elements, and are a very common form of combinator. Consider the following HTML, which represents a navigation element for a web page.

```html
<div id='navigation'>
  <ul>
    <li>Home</li>
    <li>Gallery</li>
    <li>About</li>
  </ul>
</div>
<div id='content'>
  <p>Looking for world-class steak sauce? You've come to the right place! Top reasons to buy from us:</p>
  <ol>
    <li>We use local ingredients.</li>
    <li>Perfect blend of spices.</li>
    <li>Your family will love you more.</li>
  </ol>
</div>
```

Perhaps you use `li` as both a structural element for navigation as well as a bulleted list in a document, and each needs to be styled
differently. In order to select the list items that are part of the navigation in particular, you'd use a *descendent combinator*.

```css
#navigation li {
  display: inline-block;
}
```

This selects all of the `li` elements within the `#navigation` element, regardless of how deeply the `li`'s are nested within the `#navigation` element. It will not affect the `li`'s in the `#content` section. If you want to apply a style to only the `li`'s nested immediately below the specified element, use a child combinator instead.

!video 26am74h2ai

### Child combinators: `#container > p`
Child combinators are a more specific version of descendent combinators that only apply to elements nested directly below the specified element. Consider the following HTML:

```html
<div id='container'>
  <div id='navigation'>
    <p id='welcome'>Welcome to Rigatoni, the home of pasta.</p>
    <ul>
      <li>Home</li>
      <li>Pastas</li>
      <li>About</li>
    </ul>
  </div>
  <p id='content'>Pasta is incredibly delicious.</p>
</div>
```

In this case, the CSS selector `#container > p` *will* select `#content` but will *not* select `#welcome`, since the latter is nested under another div beneath `#container`.

### Sibling combinators: `p ~ img`
Sibling combinators allow you to select items that occur at the same depth. Consider this HTML:

```html
<div id='heading'>
  <img id='logo' src='my-logo.png' />
  <p>Welcome!</p>
</div>
<div id='content'>
  <p>First paragraph.</p>
  <img id='profile-photo' src='avatar-photo.jpg' />
  <p>Second paragraph.</p>
  <p>Third paragraph.</p>
</div>
```

In this case, the `p ~ img` selector will apply styles to any `img` elements following a `p` element; the `#profile-photo` will be styled but the `#logo` will not (since the `p` comes after the `img`). However, note that if we ever add an image to the `#heading` then the rule will match there as well, so use this combinator cautiously.

### Attribute combinators: `input[type=text]`
You can also select particular elements that have a specified [attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes). This is very useful on elements that can serve multiple purposes depending on the value of a particular attribute; `input` elements are the most common example since they can represent a text field, button, checkbox, radio button, etc depending on the value of the `type` field. It's fairly rare to style a form without using attribute combinators.

However, it's important to note that the same syntax can be used for any attribute/value pair, not just the `type`. Consider some HTML:

```html
<form method='post' action='/submit'>
  <input type='text' name='name' id='name' />
  <input type='text' name='email' id='email' />
  <input type='radio' name='gender' value='Male' />
  <input type='radio' name='gender' value='Female' />
  <input type='submit' name='submit' value='Submit' />
</form>
```

The `input[type=text]` selector will select the `#name` and `#email` elements but all other input types will be ignored. This is important because each of these elements is rendered quite differently and certain styles may not apply to all elements.

!video crqjiwztxw

### Pseudo-class Combinator: `a:visited`
*Pseudo-classes* are specific states that certain elements can exist in, and need to be supported by a browser in order to work. Common pseudo-classes include `hover`, `visited`, and `active` for links, `focus` for form elements, and `first-child` and `last-child` for lists. A full list is available at the above link. You can think of pseudo-classes as being built-in classes that apply to particular elements under certain conditions (depending on the pseudo-class).

Consider the following HTML:

```html
<div id='navigation'>
  <ul>
    <li><a href='/home'>Home</a></li>
    <li><a href='/gallery'>Gallery</a></li>
    <li><a href='/artists'>Our artists</a></li>
    <li><a href='/about'>About</a></li>
  </ul>
</div>
```

A *psuedo-class selector* like `a:visited` will allow you to change how links that have already been visited should be rendered. Similarly, if you apply `li:first-child` you can apply a distinct style to the first item in the list, such as applying a border.

!video kgkam2atpz

### Pseudo-element combinator: `li::before`
*Pseudo-elements* are similar to pseudo-classes, but can be thought of as built-in *elements* that exist in relation to other elements. For example, `p::first-letter` can be used to make the first letter of a paragraph larger than other letters, and `a::after` can be used to easily render tooltips[^1].

Consider the following HTML:

```html
<div id='container'>
  <h2>Things I like</h2>
  <ol>
    <li>Dogs</li>
    <li>Coding</li>
    <li>Dogs</li>
  </ol>
</div>
```

By default, ordered lists are rendered with numbers and letters in front of the content itself, and it's difficult to style those markers. You can, however, reference them through pseudo-elements using `li::before`, or combine it with a descendent selector as `#container li::before`.[^2]

## Examples
Think through how you'd select particular elements in the HTML below. Note that the important part of this exercise is to design the appropriate selectors and combinators, not necessarily to identify the correct properties to modify on those elements (we'll cover the latter in another section!).

```html
...
<body>
  <div id='header'>
     <h2>Rapscallion Records</h2>
     <ul id='navigation'>
       <li>Home</li>
       <li>Artists</li>
       <li>Locations</li>
       <li>Who we are</li>
     </ul>
  </div>
  <div id='content'>
     <p class='summary'>We're not your grandma's record store.</p>
     <p>Rapscallion Records is Chicago's leading seller of underground jazz hits. Rockin' the beats on the streets since 1927.</p>
     <p>Come by one of our stores in the Chicago area and see for yourself.</p>
     <img src='/stores/hq.png' />
     <p>Sales on top albums until Labor Day! Don't wait!</p>
  </div>
</body>
...
```

1. What selector / combinators would you use to change the font of all elements on the page?
2. What selector / combinators would you use to change the color of the text for the `content` section?
3. What selector / combinators would you use to ensure that text wraps around images that are present in the `content` section?
4. What selector / combinators would you use to convert the unordered list in the `header` to be a horizontal list?

[^1]: https://css-tricks.com/pseudo-element-roundup/
[^2]: http://blog.teamtreehouse.com/customize-ordered-lists-pseudo-element