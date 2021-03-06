Responsive Web Design (RWD) is where we cover some basic concepts of media queries and how content should adapt to different devices and scenarios.

We cannot predict how a user will view our site, whether that will be on a mobile device or a smaller window on their giant desktop screen.  So, we have to be 'responsive' in displaying our content so that the users will have an optimal experience and be able to achieve the goals we set forth for anyone visiting our application.

Concepts:
- @media queries aka breakpoint
- device specific media queries aren't the end all be all.
- &lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt;
- definition: viewport

## The technical

One of the first things that you need to implement on your html document is a meta viewport tag, in the `<head>` of your html page.

### Viewport &lt;meta&gt; tag

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

This meta tag allows the fonts and screen widths to work with many devices without the need to double tap or pinch to zoom.

From the google devlopers documentation:

<blockquote>
<h4>TL;DR</h4>

<p>Use meta viewport tag to control the width and scaling of the browsers viewport.</p>

<p>Include width=device-width to match the screen's width in device independent pixels.</p>

<p>Include initial-scale=1 to establish a 1:1 relationship between CSS pixels and device independent pixels.</p>

<p>Ensure your page is accessible by not disabling user scaling.</p>
[Google Dev Docs](https://developers.google.com/web/fundamentals/layouts/rwd-fundamentals/set-the-viewport?hl=en)
</blockquote>

Aside from focusing on the content of your site, one of the biggest tools as a web developer making a responsive site is the ability to adjust layout, fonts, display of said content as your viewport changes for different devices and screen sizes

### Responsive @media queries

<blockquote>
Media queries are simple filters that can be applied to CSS styles. They make it easy to change styles based on the characteristics of the device rendering the content, including the display type, width, height, orientation and even resolution.
</blockquote>

The use of @media queries is pretty straightforward; you apply them to gracefully adjust your content using various dimensions such as:

- display type
- width
- height
- orientation
- resolution

An example of a few media queries:

```css

body {
  background-color: green;
}

@media screen and (max-width: 320px) {
  body {
    background-color: blue;
  }
}

@media screen and (min-width:450px) and (max-width: 550px) {
  body {
    background-color: red;
  }
}

```
In the example above, you see where the body's background is styled 3 times.  

1. body background is green if the @media query is not overriding, meaning the background of the body will be green when the width is at 321px up to 449px and also whenever the viewport is > 550px;
2. The first @media query basically says in plain language: apply any of the styles contained within my screen as long as they do not exceed my max width of 320 pixels.  This means that a 0 - 320px device width will cause the body's background to be blue
3. The final media query states: apply any styles contained within my screen when I at least have a width of 450px and am less than 550px and no more.

## A few words about content

A responsive site will not be effective unless there is a lot of consideration into how the content will adapt to the different devices and viewport sizes.

Simply creating @media queries to stack content in a smaller screen will not make it more usable or enhance the experience alone.

Instead, adjust your site/application by testing in different devices and try to understand when your content is no longer usable or able to be accessible.  

This is often (and very simply stated by me) referring to a content-first strategy.  Meaning, you need to think about your content beforehand and how it will be used.

If you design your interface with small viewports in mind from the beginning, you'll also start to see how more maintainable your site will be come while users enjoy the main goals of your application without structure getting in the way to over complicate things


## Resources

[RWD Checklist](http://rwdchecklist.com/)

[Responsive Design Basics](https://developers.google.com/web/fundamentals/layouts/rwd-fundamentals/)

[320 and Up - good starting point](http://stuffandnonsense.co.uk/projects/320andup//)

[Responsive Patterns](http://bradfrost.github.io/this-is-responsive/patterns.html)