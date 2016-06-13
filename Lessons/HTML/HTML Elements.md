## The Importance of Content
We've covered the basics of a web page - the required elements, content, and metadata, and how to include other resources in your page. Let's get to the fun stuff now: your own content! HTML content provides the scaffold for your whole web page and is where your creativity really gets to come out.

It's important to remember as we start learning how to add content that HTML is intended to be your web page's skeleton. When designing the HTML for your web page, you should be concerned about intent and purpose, not color, shape or size.[^1]

## The Document Object Model (DOM)
Before we dive in, let's get a clearer understanding of how HTML is interpreted by your browser. Web browsers implement what's called the [Document Object Model](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model), or "DOM", as the basis for interpreting content like HTML, XML, and SVG. The DOM is defined by the [W3C](http://www.w3.org) and can vary a little bit between browsers. It defines a "tree" structure for our webpage, resulting in "parent" and "child" elements. It also defines our events and lets us watch for them. This is critical for us when using JavaScript, as the DOM is the interface we use to target elements and watch for events.

## Attributes & Special Content
Let's discuss another important part of an HTML element: *Attributes*. We've seen attributes in some of our examples but haven't discussed them in-depth yet.

HTML elements often need data beyond their content. To supply this data, we can use "key-value" pairs inside the opening tag of the element. These pairs are referred to as "attributes" and use the following patten: `key="value"`. Attributes are optional for some elements and mandatory for others. Here's an example of an anchor element using attributes:
```html
<a href="http://www.theironyard.com">The Iron Yard's Homepage</a>
```
Generally, consider the purpose of the element you're using - does it need extra data to fulfill its purpose? It probably has mandatory attributes to provide that data. You can read more about HTML attributes at the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes).

Let's look at two very common elements that require the right attributes to function properly: anchor & images.

  - `a`: The `a` element, short for "*anchor*", provides a hyperlink to another web page or to another location on the current web page. Hyperlinks are the backbone of the Web and make it possible to easily navigate between content. Hyperlinks (usually just called "links") require an "*href*" attribute ("Hypertext REFerence") so that they know where to direct the user when they're clicked. The anchor element will generally be rendered as its content, but distinctly colored and sometimes underlined. An `a` element without an `href` attribute does nothing - it will be styled in a special way, but acts like plain content otherwise.[^2]

Example:
```html
<p>Click <a href="www.theironyard.com">here</a> to visit The Iron Yard's homepage.</p>
```

  - `img`: `img` is an abbreviation of "image", and provides the ability to add pictures to your webpage. The `img` element requires a `src` ("SouRCe") attribute pointing at the desired image's location. This can be on your current server or on another web page. It's not required, but it's always a good idea to include the `alt` attribute as well. `Alt` provides "ALTernative" text that will be displayed if your image can't load or will be read out loud as a description of the image for people who can not see.[^3] `img` is a void element and doesn't use a closing tag.

Example:
```html
<img src="red-panda.jpeg" alt="Adorable red panda cub laying in grass.">
<a href="cool-site.com"><img src="link-image.png" alt="Images can be links, too!"></a>
```

Besides the mandatory attributes some elements require, there are some very common attributes that most elements can accept. The most often-seen of these are `class` and `id`. The `id` attribute provides an identifier that an element can be referred to by. The value of `id` must be unique for each element that has this attribute. `Class`, on the other hand, can be shared across many elements. Both of these attributes are often used to help identify elements we want to style or target for interactivity with external resources.

Example:
```html
<a href="my-cool-site.com" class="special-red-link" id="my-first-link">Link #1</a>
<a href="another-page.org" class="special-red-link" id="my-second-link">Link #2</a>
```

## Text Content
The most common type of content on the Web is text. Every site needs text, whether it's a news article, an image caption or a dynamic chatroom. Let's talk about the different types of common text elements.

  - `p`: We've seen this element already. `p` stands for "paragraph" and is intended for independent portions of text. Paragraph elements will often include extra space before and after the element when they're rendered.

Example:
 ```html
<p>This is a paragraph of text. It can just be one sentence or a whole bunch of sentences.</p>
<p>Here's a another paragraph element. See how these two elements are spaced apart?</p>
```

- `h1, h2, h3, h4, h5, h6`: "H" stands for "Header". These `h`-elements (1-6) are intended to be headers for your web page or individual sections of it. `H1` is the largest of the header elements and should be reserved for top-level headers, while `H2` - `H6` get progressively smaller by default and are intended for subsections or content titles. 

Example:
```html
<h1>HEADERS</h1>
<h2>Why use headers?</h2>
<p>Headers are used for content that should be extra-visible and is important for labelling your page's content.</p>
<h3>Header sizes</h3>
<p>The size of each header will vary across browsers.</h3>
<h3>REMEMBER</h3>
<p>Headers should be used to indicate titles & sections, NOT just for bigger/smaller text!</p>
```

- `span`: The "span" element lets you select text "inline", or embedded within other elements. Span elements are often used to single out words that will need to be styled or acted on by an external resource (like CSS or Javascript).

Example:
```html
<p>We'll style <span class="first">this text</span> as red and <span class="second">this text</span> as blue.</p>
```

- `pre`: Pre elements are used for displaying "preformatted" text. This means text that won't get the default styling from your browser. Pre elements are most often used for displaying code in your web page.

Example:
```html
<p>Let's look at some code:</p>
<pre>
  <h3>SAMPLE CODE</h3>
  <p>Here's some sample code.</p>
</pre>
<p>That was a great sample!</p>
```

- `blockquote`: Block quotation elements are used to indicate a quoted block of text. This is generally rendered as indented on your web page to indicate that it should stand alone.

Example:
```html
<p>Consider this quote from Edward Dijkstra:</p>
<blockquote>Simplicity is prerequisite for reliability</blockquote>
<p>It's good to remember to keep your code simple so others can work on it.</p>
```

- `em` and `strong`: These two elements are both used to note important content, but each act in a different way. The *em* element is intended to provide emphasis to a piece of text and generally renders italicized. The *strong* element notes text as extremely important and is often rendered as bold text. The difference is subtle but important to distinguish how wrapped text is intended. 

Example:
```html
<p><strong>WARNING</strong>: Acid will burn you. Do <em>not</em> drink any acid.</p>
```

- `br`: The "*break*" element isn't strictly a text element, but it's used with text content. `br` inserts a line break in your web page. It shouldn't used to simply separate text (that's what a new `p` element is for), nor should it be used for pushing elements down in your layout (we'll discuss better ways to do this soon).  However, within a paragraph element, `br` is an effective way to separate content. `br` is a void element, so it doesn't use a closing tag. This element should be used sparingly. 

Example:
```html
<p>
  Here's a bunch of text. We're including a super important link we want on its own line.
  <br>
  <a href="http://www.important-site.com">Important Link</a>
  <br>
  We can use the break element to put the link on its own line without all the extra spacing new paragraph elements would cause.
</p>
```

#### Word Search
###### Let's look through a live web page to find some examples of text content in the wild.
!video 4j194ukd91

## Lists

HTML provides us with a few great ways of listing our content in an organized manner.

The `ol`, or "Ordered List" element, creates a numbered list of items, while the `ul` ("Unordered List") element simply bullets the items. Both elements accept nested `li` ("List Item") elements as members of their lists. Lists can be nested within other lists and can accept as many list items as you'd like to include. List items can accept any valid HTML as content, including pictures and other lists! [Shay Howe's site](http://learn.shayhowe.com/html-css/creating-lists/) provides a much deeper dive into HTML lists.

Example:
```html
<h3>Steps To Make Dinner</h3>
<ol>
  <li>Look in your refrigerator.</li>
  <li>Call the pizza place.</li>
  <li>Wait for the delivery person.</li>
</ol>

<h3>Things You'll Need</h3>
<ul>
  <li>A refrigerator</li>
  <li>A phone</li>
  <li>A wallet with money.</li>
</ul>
```

## Content Containment

Part of HTML's purpose is to provide a scaffold for your web page.[^5] This means content should be organized in a logical manner, and HTML provides lots of tools to help us accomplish this effectively. Without utilizing other resources like CSS, HTML provides us with a single shape to work with: a rectangle. We refer to HTML's invisible organizational rectangles as "divisions", or `div`s. `div` elements extend fully across the web page and allow you to organize content based on its purpose or location on the web page. `Div` elements aren't visible without styling. Most divs will include attributes that aid in styling them.

Example:
```html
<div class="header">
  <p>This is a distinct section of our page.</p>
</div>
<div class="content">
  <h1>SHINY NEW SECTION</h1>
  <p>Here's the next region of our page.</p>
</div>
```

## Semantic HTML
`div` elements provide us the freedom to separate our web page's content however we see fit, but it can get tiring having to type out descriptions of all of our divs as attributes. The managing body behind HTML's specifications saw this as a limitation and introduced some great new elements with HTML 5 (the latest iteration of rules for dealing with HTML).[^6] We refer to these new elements as "semantic" because they use plain English to communicate their purpose, instead of "div" and "my-new-page-header". Let's take a look at some of these.
  - `header`: The header element refers to a collection of content at the top of your web page. Headers may be shared across multiple pages within a website. Note that this is a content-filled header; it's not related to the `head` element we've seen in the structure of your webpage.
  - `nav`: The nav (short for "navigation") element contains links or menus used for getting around your web page or website.
  - `main`: The "main" element contains (as its name suggests) the main content for your page. Use `main` to indicate where your web page's unique content resides.
  - `article`: The "article" element refers to any portion of your website that might be reprinted elsewhere. It's not just limited to news articles! Use `article` for blog posts, comments, unique components or even images with their captions.
  - `section`: Section is meant for a unique division of your web page. Sections usually include at least one header and represent a portion of your content. A section of your web page might be devoted to a particular theme and contain multiple articles.
  - `aside`: An "aside" element is used to contain "sidebar" content. This might be reserved for advertisements or might contain commentary on your webpage's "main" section.
  - `footer`: The "footer" element acts as the lower anchor for your web page and groups content meant for the bottom. Footers, like headers, are often shared across web pages to provide a common theme for a website.
There are lots of good reasons to prefer these semantic HTML elements over simple `div`s. Besides making your code easier for other developers to read, semantic HTML makes your page MUCH more accessible to those with disabilities. Visitors who use screenreaders or special tools to interpret your webpage based on their impairment will be thankful that your webpage relies on the latest standards. This should always be a consideration when designing a web page. You can learn a whole lot more about semantic HTML and why we use it from [this excellent Smashing Magazine article](http://www.smashingmagazine.com/2013/01/the-importance-of-sections/).

#### Divs & Semantic Layout
###### We'll examine a few popular websites to see how they employ divs and semantic HTML elements to create logical divisions.
!video e7r3d7i8aa

[^1]:http://www.motive.co.nz/glossary/markup.php#html
[^2]:http://www.w3.org/MarkUp/1995-archive/Elements/A.html
[^3]:http://accessibility.psu.edu/images/imageshtml/
[^5]:http://www.quepublishing.com/articles/article.aspx?p=24021
[^6]:http://www.w3.org/TR/html5/sections.html