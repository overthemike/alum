## Everyday CSS properties
It's worth being generally familiar with most CSS properties, but you'll save a lot of time by memorizing some key properties that you're going to use over and over again. The following section outlines common CSS properties.

### Styling content: fonts
How text is presented greatly affects readability. CSS supports highly granular customization of text styles, including changing font families, font size, kerning, and weights.

- `font-family`: sets the font face used for text. This can be a specific font (e.g.: "Garamond", "Helvetica Neue"), a generic font family (e.g.: "serif", "monospace"), or a list of multiple choices. If multiple choices are given, the browser will go down the list until it finds a font that is available on the system, or fall back to the default font family if none of the font choices are available. For this reason, it's always good to end your `font-family` declarations with a generic font family. 
- `font-size`: the size of the text, which can be specified in several different ways: percentage, `em` or pixels.  
- `font-style`: used to set a font to either `italic` or `oblique`. 
- `font-weight`: sets the weight of a font. This can be just `bold`, or exact weight values (`100` - `900`, in increments of 100) for fonts that offer them. 

There are a few ways to import custom fonts. Browsers have built-in "web-safe" fonts that are generally available, and are usually highly readable but generic. Services like [Google Fonts](https://www.google.com/fonts) provide fonts that can be imported as external resources. There's also a `@font-face` rule in CSS3 that supports custom fonts (loaded from your own external font files).

### Styling space: layouts and box sizes
Layouts are perhaps the most error-prone CSS-related task and there are a lot of tools and best practices to be aware of. The CSS Layouts lesson covers both properties and practices related to CSS-based layouts. In short, important properties for layout-related tasks include:

- `display`: determines how the element's box will be positioned relative to other boxes
- `margin`: sets the margin around the element's box. You can provide a single value to `margin` to set the margin on all sides, or specify a specific side with `margin-top`, `margin-bottom`, `margin-left`, and `margin-right`. 
- `padding`: sets the padding around the element's box. This functions identically to `margin` - you can provide a single value or a specific side (`padding-top`, `padding-bottom`, `padding-left`, or `padding-right`).
- `width` and `height`: used to specify sizes of boxes (exact behavior depends on `display` value). `min-width`, `max-width`, `min-height`, and `max-height` are also helpful for sizing, especially for making layouts that accommodate a variety of screen sizes.

Make sure to read the section on relative and absolute sizing in the CSS Layouts lesson to understand the various types of units these properties can be specified in and the pros and cons of each.

### Styling transitions: animations
Not all projects will have animations, but sometimes even subtle animations can have a surprisingly positive impact on the user experience. CSS3 adds many new tools for defining and managing animations. Particular animation effects are defined using the `@keyframes` at-rule, and then applied using some core animation properties, including:

- `animation-name`: the name of the animation that should be applied (defined with a `@keyframes` at-rule; see below).
- `animation-duration`: how long the animation should last in seconds or milliseconds. Note that animations will be interpolated across this duration so longer durations lead to a slower animation.
- `animation-timing-function`: how the animation should progress over the course of the duration; a value of `linear` will make the animation progress between keyframes at a constant pace, and various ease in / ease out variants are also available.

The `@keyframes` at-rule is a flexible way to define custom animations, and uses existing CSS properties to define "states" of an animation. Once defined, a particular animation can be applied to any number of selectors. An example `@keyframes` at-rule that changes the background color might look like:

```css
@keyframes colorshift {
    0% {
        background-color: red;
    }
    50% {
        background-color: green;
    }
    100% {
        background-color: blue;
    }
}
```

Any properties related to animations can then be applied to rules that set `animation-name: colorshift`. Note that keyframes are covered in detail in the CSS Animations lesson.

## Shorthand properties
*Shorthand properties* are a concise way to represent multiple related properties at once. For example, the `border` property allows us to configure values for `border-width`, `border-color`, and `border-style`. They're a convenient and quick approach to writing CSS, and also reduce the amount of information that needs to be sent to a user's browser. Using shorthand properties is usually a good idea, though there are a few gotchas to be aware of[^1]. The full list of shorthand properties includes:

- `animation`
- `background`
- `border`
- `font`
- `margin`
- `padding`

Certain properties also allow *shorthand values*. This means the way a shorthand property is applied is determined by the number of values used. For example, `margin` can be written as:

- `margin: 2em` - a margin of 2em on each side
- `margin: 2em 3em` - a margin of 2em on the top and bottom, and 3em on the left and right
- `margin: 2em 3em 4em` - a margin of 2em on the top, 3em on the left and right, and 4em on the bottom (uncommon form)
- `margin: 2em 3em 4em 5em` - a margin of 2em on top, 3em on the right, 4em on the bottom, and 5em on the left. Note that this moves in a clockwise direction, starting at the top.

## Common problems
The syntax of CSS is somewhat straightforward, but there are a number of places where developers can run into issues. Here are some common problems to look for if you're running into trouble:

- Make sure you're including semicolons at the end of all declarations. If you forget to include semicolons then properties after the forgotten semicolon may be ignored. Note that while it's not strictly necessary to add a semicolon after the last property in a rule, there's no reason not to and can prevent errors from occurring when you need to add new properties to the rule.
- Remember that browsers aren't consistent with their default CSS values, so just because something renders one way on your laptop doesn't mean it's going to look like that for everyone. Be explicit, and use a CSS reset to make sure that most defaults will be consistent across browsers.
- Remember that CSS assigns priority to selectors, called *specificity*. If a rule isn't being applied correctly, ensure that it's not being overwritten by another rule with higher specificity.

[^1]:https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties#Tricky_edge_cases