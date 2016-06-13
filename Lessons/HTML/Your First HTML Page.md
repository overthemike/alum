## What is "HTML"? 

HTML stands for "HyperText Markup Language". It acts as the skeleton of a web page, providing the underlying structure. HTML does not define either decorative or functional qualities of your page (like colors or animations). Instead, it uses "elements" to build up a scaffold that you can style and interact with using other languages.[^1] 

Before we get started with our first web page, let's take a brief tour of how HTML works. HTML documents are composed of "elements". An element acts as a simple instruction to either display or prepare for a particular type of content. Some elements may be invisible and are used only for the benefit of your browser, while others display content, like text or images, on your web page.

Elements are composed of "tags". Tags are the actual words we use to communicate in HTML. A tag is made up of an "opening bracket" (`<`), the name of the tag, and a closing bracket (`>`).

Most elements follow the structure of an "Opening tag", then "Content", then a "Closing tag". When following this format, we prefix the name of the closing tag with a `/`, to indicate that we're closing an element. Elements can stand by themselves or be "nested" within other elements. Nested elements have a "parent-child" relationship, meaning that we refer to the enclosing element as the "parent" and the nested element as the "child". We denote this nesting using indentation to make it easier for humans to read. Here are a couple simple elements:

```html
<p>My first element</p>

<section>
  <h3>
    I am the content of the "h3" element.
    The "h3" element is a "child" of the "section" element.
    The "section" element is the "parent" of the "h3" element.
    Notice how we indent to show these relationships.
  </h3>
</section>
```  

There are some elements that don't require content or a closing tag. We call these "*empty elements*" or "*void elements*".[^2] A void element will have only one tag that looks just like an opening tag. Void elements don't accept content, which distinguishes them from typical elements. Some elements are not void but have optional content, resulting in opening & closing tags with no content between them. These are still considered standard elements, and still require both opening and closing tags. Void elements are less common but still important to recognize. Here's a simple void element you'll use frequently - an `img` element, used to include images in your web pages:

```html
<img src="http://www.my.image.com" alt="My Cool image">
```

It's important to note that the term "element" refers to a set of related tags and their content.[^3] To help reinforce this distinction, it's good practice to avoid using the word "tag" by itself - refer to "opening tags", "closing tags" and "void tags" instead. This is a great way to reduce ambiguity when describing a problem to another developer.

  ![TODO - Elements vs. Tags](https://s3-us-west-2.amazonaws.com/tiy-learn-lesson-assets/images/html/elements-vs-tags.png)

## Our First Web Page

We'll write our first web pages completely from scratch. To get started, open up your text editor and create a new file. We'll name this file "index.html". "index" is a common name for the first page of a website[^4], and the ".html" suffix lets your computer know that this document should be interpreted as a web page[^5]. Type (don't copy/paste) the following content into your editor exactly as it's displayed below:

```html
<!doctype html>
<html>
  <head>
    <title>My First Web Page</title>
  </head>
  <body>
    <!-- Content goes below here. -->
    <p>My first web page text.</p>
  </body>
</html>
```

Now, if you open this document with your web browser, you should see a white page with plain black text. Congratulations, you've created your first web page!

Let's walk through your first code line by line to understand what's going on:

 -  `<!doctype html>`: DOCTYPE elements are a special element that should go at the top of every web page you write. This line tells the browser that the rest of the document should be interpreted as HTML. It's a little funny looking, but will save you a load of headaches down the road.[^6] "DOCTYPE" is a void element, which means it doesn't need a closing tag. Be sure not to forget the "!" before the word "doctype". 
 -  `<html>`: This is the start of your web page. All web pages are defined within an "*html*" element.
 -  `<head>`: "*head*" is a special element that contains information your web browser needs to display your web page correctly. Your visitors won't see most of the data inside your head tag. Content here may include information about the web page's author, language, or external files that the web page needs to load, like "stylesheets" or "scripts".
 -  `<title>My First Web Page</title>`: This is our first full element. The "*title*" element directs your web browser on how to refer to this web page. If you look at the top of your browser, or inside the tab itself, you should see "My First Web Page". This is the title element in action. Every web page needs a descriptive title, since it will be used in search results, browser history, and saved bookmarks.[^7] Notice how we open the element with an opening tag, add our content (just some text in this case), and then use a closing tag (denoted by that `/`) to close the element.
 -  `</head>`: Since we're done with our Head content, we need to close the Head element.
 -  `<body>`: The "*body*" element contains the main content of your web page. This is where you'll put content you want your visitors to see. The body element is where you'll do 99% of your work when building websites.
 - `<!-- Content goes below here -->`: This is an HTML "*comment*". Comments don't show up on your webpage but remain in your source code. They provide a great way of adding notes for yourself or other developers to clarify what a bit of code does. HTML comments start with a `<!--`, can cross any number of lines, and end with a `-->`.
 -  `<p>My first web page text.</p>`: This is our first text content. The `<p>` element, also known as the "*paragraph element*", creates a standalone block of text. It relies on the default browser styles and is great for simple messages or larger blocks of text content on your web page.
 - `</body>`: This closes our body element.
 - `</html>`: Finally, we can close our "*html*" element. As you can see, the entire page is encapsulated inside the html element. This is standard practice for web pages.
Before we wrap up, let's add our own text content. Whenever we add content to a web page, it's good practice to make sure it's part of the appropriate element. For simple text, we'll revisit the `<p>` element. Add a `<p>` element to your web page containing whatever text you'd like. Make sure you include both the opening and closing tag for your paragraph element.

Traditionally, a programmer's first program should print the words "Hello, world."[^8] Sometimes it's fun to break the rules, so feel free to write whatever you'd like on your web page. You'll want to add your text to your `<body>` element. Your page will look like this (with whatever text you choose):
```html
<!doctype html>
<html>
  <head>
    <title>My First Web Page</title>
  </head>
  <body>
    <!-- Content goes below here. -->
    <p>My first website text.</p>
    <p>I added this text myself!</p>
  </body>
</html>
```

Save your changes and either open your `.html` in your browser again or, if it's already opened, use the "Refresh" button to reload the page and see your changes. You should see your text on the page. Hooray! You've completed your first web page.

#### Webpage Workflow
!video e839g1qn39
<!-- a quick walkthrough of opening a text editor and creating a new "index.html" file, then opening it in a browser after saving. -->

## Including Other Resources

Let's cover one more topic before we wrap up: external resources. As we discussed previously, HTML acts like the skeleton for your page. However, there's more to your web page than the skeleton - you probably want to add a nice design and some dynamic functionality for your users. We use different languages for different purposes in web development. HTML is for structure, CSS is for styling our page (adding colors, fonts, borders, etc) and JavaScript is for functionality (dynamic content & user input). It's good practice to keep content written in different languages in separate files. That way, changes can be made independently.[^9] This lets you share one resource across multiple web pages, minimizing the work you'll need to do to update or modify a website. 

Thankfully, HTML gives us an easy way to let our web browser know where to find the extra files our web page depends on. The "*link*" element[^10] is used to point to CSS "*stylesheets*" (files written in the CSS language that define the styles for your web page). `Link` is a void element, which means it only needs a single void tag and not an opening & closing tag like most elements. `Link` belongs inside the `head` element of your page and usually uses two "*attributes*" (extra data about the element included inside a tag):
  
  - `href`: "*href*" is short for "hypertext reference" and refers to the address of the file you're linking. This is sometimes called the `link` element's "target". 
  - `rel`: "*rel*" is short for "relationship" and defines the relationship between your HTML and the link element's target.  
Here's an example of a `link` element you'll see frequently:
```html
<link rel="stylesheet" href="styles.css">
```

#### External Resources
!video zoptjqnpaa
<!-- Walk through adding a CSS file to a drab web page with the link element to demonstrate how much of a difference external files can make to a website's form & function. -->


[^1]:https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Introduction#What_is_HTML
[^2]:http://www.w3.org/TR/html-markup/syntax.html#syntax-elements
[^3]:http://www.w3.org/TR/REC-html40/intro/sgmltut.html#h-3.2.1
[^4]:http://www.htmlgoodies.com/beyond/webmaster/article.php/3473251/Index-or-Default.htm
[^5]:https://en.wikipedia.org/wiki/List_of_file_formats
[^6]:https://developer.mozilla.org/en-US/docs/Glossary/Doctype
[^7]:http://reference.sitepoint.com/html/title
[^8]:http://stackoverflow.com/questions/602237/where-does-hello-world-come-from
[^9]:http://www.w3.org/community/webed/wiki/The_web_standards_model_-_HTML_CSS_and_JavaScript
[^10]:https://developer.mozilla.org/en-US/docs/Web/HTML/Element/link
