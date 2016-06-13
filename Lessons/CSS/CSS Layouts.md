In addition to styling, one of the most important capabilities of CSS is the ability to define flexible layouts for our content. Layouts have a tremendous impact on the usability of a website and designing something that will work across the full range of browsers and devices takes some practice and awareness of common challenges and pitfalls. Best practices for web design have evolved dramatically over the past couple of decades, largely driven by emerging standards (like CSS) and the emergence of new devices; popular browsers are making a steadfast push to support standards as well.[^1]

Once completed, a well-designed layout will make it possible to add and modify content without needing to adjust the layout to accommodate the new material. In this section we'll review the building blocks that CSS provides for modern CSS-based layouts, as well as some of the theory behind how to define flexible layouts in today's multi-device world.

## Common CSS properties
Generally speaking, the art of creating an effective layout involves specifying positions of elements, as well as how those elements should adjust under different circumstances (changing screen / window dimensions, for example). Elements are defined by a *bounding box* that occupies a location in your layout. CSS layout properties are all about defining the location and interaction between elements' bounding boxes. Standards and availability in modern browsers is evolving rapidly, but certain properties are in widespread use today.[^2]

### The box model
The "bounding boxes" referred to above are a part of the *box model* used for specifying the size and position of all HTML elements. All HTML elements are rendered in the document as a box with a certain width and height. Each element's box is made up of a series of smaller nested boxes.

![The box model, courtesy of Mozilla Contributors at https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model](https://mdn.mozillademos.org/files/8685/boxmodel-\(3\).png)

There are four smaller boxes that make up each element's box, each of which can be sized using CSS properties.
- The *core content area* is where text, images, etc will appear. This is the innermost box and can be sized using `width` and `height` rules.
- The *padding* is the blank space between the content and the border, and can help give individual elements breathing room beside the rest of the content on the page. Padding can be adjusted using `padding` rules.
- The *border* is the region that marks the visual edge of the box; the `background-color` of the box, for example, will not extend beyond the border. The border's width, color, and style can be adjusted all at once using the single `border` shorthand property, or individually using `border-width`, `border-style`, and `border-color`.
- Last but not least, the *margin* is the blank space between the border of the element and the next element. Margins are similar to padding but are positioned outside of the visual area of the element. Margins can be styled using the `margin` property.

When it comes to specifying sizes, both *absolute* (`px`) and *relative* (`%` and `em`) are usually valid but make sense in different circumstances. Make a conscious decision about which should be used based on what you're trying to accomplish and be consistent unless you have a good reason not to be. When it comes to layouts, relative sizes are often preferred since they'll accommodate a broad range of screen sizes.

### Display
The CSS specification states that the `display` property defines, among other things, how the box participates in the parent formatting context. In other words, it defines the element's *role* in the layout. There are two primary roles: `block` (meaning it occupies the entire horizontal space, such as a section of a page or container) and `inline` (meaning it occupies a portion of the horizontal space, such as column of text or embedded image).

- `display: block` - the element should, by default, start on a new line and occupy the full width of the parent element, but also respect explicit `width` and `height` values. This is the default for elements like `div`, `p`, and the header elements (`h1`, `h2`, etc).
- `display: inline` - the element should, by default, occupy only the required amount of space to present all of its content. Other content can be placed before or after it horizontally. Inline elements cannot have an explicitly defined `width` or `height`. This is the default for elements like `span` and `a`.
- `display: inline-block` - a useful hybrid of block and inline display types, which allows for `width` and `height` to be specified but will also allow other elements to appear before or after it horizontally. This is the default for elements like `button` and `select`.
- `display: none` - the element should not be visible and should not occupy space in the layout. Note that there is also a `visibility` property that can also hide items, though they will still occupy space. `display: none` is sometimes useful in combination with Javascript to make certain elements visible or invisible depending on the state of the application (hiding a menu until the "menu" button is clicked, for example). This is the default for elements like `script` and `meta`.
- `display: flex` - a newer property on the scene that can be a bit harder to find dependable resources on. Flex, or *flexbox*, properties approach layouts slightly differently and allow child elements to be ordered, wrapped, sized, and aligned relative to other elements in the same flexbox.[^3] 

### Position
The `position` property, along with `float`, is used to define how an object's location is described to the browser. All elements default to `position: static`, but this can almost always be changed if needed. Once changed, the position is described using the `top`, `bottom`, `left`, and `right` (positional) properties.

- `position: static` - positional properties are ignored and the element is rendered in its "normal" position according to its `display` type.
- `position: relative` - the box's normal position is computed and then adjusted by the positional values specified. For example, a box that was going to appear 300px from the left that's got `left: 100px` would be rendered 400px from the left.
- `position: absolute` - the box's normal position is *ignored* and overwritten by the provided positional values. They are taken out of the normal flow and do not affect other elements.
- `position: fixed` - the box's position is treated just like `position: absolute`, but will also be locked to that position with respect to a particular point of reference (usually the browser's viewport), meaning that the element will maintain it's position even if the user scrolls.

### Float
The float property, like the `position` property above, describes how the browser should interpret the positioning of the element. `float` is used for extracting elements from the normal flow and moving them to the left or right of other elements in their parent's box. For example, wrapping text around an inline image is typically achieved by `float`ing the image.

`float: left` means that the element should be moved to the left of non-float content, and `float: right` means that it should be moved to the right of non-float content. Floats will move in the specified direction until they reach the edge of the box or another floating element.

Floats are often used to create multi-column layouts or to position particular elements. Note that you'll need to be familiar with the `clear` property (introduced below) if you want to use flows to define page layouts.

### Clear
The clear property is used for indicating to the browser how a particular element should position itself relative to nearby floating elements. It's used exclusively in conjunction with the `float` element above, though they're usually applied to different elements.

`clear: left` means the element should be positioned below elements that are `float: left`, and `clear:right` is the same for elements that are `float: right`. You can also specify `clear: both`, which covers both cases.

### Margin and Padding
`margin` is the space around the outside of a box that should not be used for other boxes; it will be rendered as whitespace between the border of the box and the next element.

`padding` is the space between the content of the box and the border that should not be used for other content; it too will be rendered as whitespace, though *inside* of the border in this case.

Another useful trick: when the `auto` value is specified, the `margin` property will split the available space between left and right margins, effectively centering the element. This is handy trick and usually the easiest way to center block-level elements horizontally.

### Min and Max
Sometimes it's useful to be able to specify minimum or maximum heights and widths. For example, if you specify that the navigation bar on your website should be `30%` of the page width, all is fine and dandy until someone views the page on their watch and 30% becomes a very small amount of space. In cases like this, you'll often want to define a `min-width` to ensure there's at least X pixels available. This will work alongside a defined `width` (or `height` in the case of the min/max height properties).

## Responsive web design
Often the hard part of implementing great layouts isn't finding the right CSS properties, but instead can be developing styles that work on all of the browsers and devices that your users may be visiting on. Responsive web design is a popular approach outlining how you can approach your layouts to work on as many devices as possible with relatively little implementation overhead. Note that the features used to make a site "responsive" are not specific to responsive designs, but can be used together very effectively.

Going by the books, the three core features of responsive web design are:
- Measure in ratios (the "flexible grid")
- Flexible images and media
- Media queries

You can consolidate this into two best practices that encompass responsive design:
- Define all sizes as ratios so that they can scale up or down with the screen size. For fonts, this means using `em` and `%`, not `px`. For layouts (columns, margins, padding, etc) this means using `%`, not `px`. For images, make sure they stay in their containers; `max-width: 100%` will usually accomplish this. This practice will allow your design to account for a lot of variability between window sizes that occurs in the wilds of the open internet.
- Under certain conditions (very small screens like certain phones, or very large ones like TV's) a single layout may not work well; this usually goes beyond an issue of scaling and requires alternative designs. You can use *media queries* to identify properties like the current width of the browser and trigger different styles based on the value. One common practice is to hide or stack columns on thinner screens; the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) page does this. In both of these cases many styles stay the same (fonts, colors, other styling) but the layout adjusts dynamically based on the size of the window and works well across a variety of device sizes.

Putting these two pieces together lets you accommodate for both dramatically different viewing environments (via media queries) and smaller variations within each environment (via fluid, ratio-based sizing).[^4]

From a workflow perspective, many people prefer to start with the most constrained designs first (usually meaning the smallest screen size that you care about) because it forces you to think about what content is most important and reduces the probability of needing to do a design rework when you go from a larger to smaller design. As always, do what makes sense in your circumstance but this often saves headaches down the road.

[^1]: You can get a quick history of [the evolution of web design best practices here](http://sixrevisions.com/web_design/the-evolution-of-web-design) if you're interested in seeing how far we've come.
[^2]: [Learnlayout.com](http://learnlayout.com/) is one of the best resources out there at the moment for learning the most important CSS layout properties. 
[^3]: [Here's a pretty solid guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) to different flex-related properties.
[^4]: You can find a bunch of examples of responsive designs at [http://mediaqueri.es/](http://mediaqueri.es/), as well as [https://responsivedesign.is/examples](https://responsivedesign.is/examples).
