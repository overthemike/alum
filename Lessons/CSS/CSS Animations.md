Many animations can be represented in pure CSS using either *transitions* or the `animation` property. CSS *transforms* modify the position, rotation, or shape of an element and are often combined with animations to create effects. Note that more complex animations may require Javascript; Javascript-based animations can be made to do almost anything, but come at the cost of increased complexity. This lesson will only cover CSS-based animations.

## CSS transitions
Transitions are animations that occur between element states (often but not always pseudo-classes, such as `:hover` or `:active`). Expanding a navigation menu or animating a button when it's clicked are common examples of transition effects. Note that transitions do not allow you to define keyframes or looping animations; see the section on the `animation` property below for more information on creating more complex animations that can take advantage of these techniques.

Implementing a transition is done by defining the two states along with a `transition` on the base state. For example, the two states for a button could look like:

```css
/**
 * The starting (base) state that describes the button when it's not being clicked.
 */
input[type=button] {
    background-color: blue;
    border: 2px solid white;
    font-family: 'Open Sans', sans-serif;
        
    transition: background-color .5s, border .5s;
}
    
/**
 * The end (activated) state, such as the button being clicked.
 */
input[type=button]:active {
    background-color: green;
    border: 2px solid #ccc;
}
```

When a user clicks a button, the `transition` property describes the properties that should be animated when buttons change state. In this case, the `background-color` will change from blue to green over the course of 500ms whenever the user clicks a button. When the button is no longer active, it will transition back to its starting state. Note that only properties listed in the `transition` property will be affected by the transition.

When combined with Javascript, you can also add other types of transitions by applying actual classes (vs only pre-existing pseudo-classes). This is done exactly as above, but the end state would be something like:

```css
.highlight-button {
    background-color: red;
}
```
You can then add the `highlight-button` class to any button element and it'll transition to a red background until the class is removed, at which point it'll transition back to the starting state.

## Animations and transitions
More complex animations are available via the `animation` property. In particular, animations have a few key differences over transitions:

- Transitions necessarily have start and end states; animations don't have to. For example, if you want to have an image that continuously moves across the screen then animations will be a better tool for the job. 
- Animations give you fine-grained control over the animation using *keyframes*.

Note that you can often create the same effect using animations or transitions; animations are typically more expressive (you can design many different types of animations), but transitions are often simpler to express.

## Creating an animation
There are two key components of an animation: the keyframe declaration (which describes what the animation looks like) and the `animation` property (which describes what elements will be animated and some parameters of the animation, such as the duration). 

Animations can be triggered either when the page is loaded by applying the `animation` to the elements themselves, or triggered using Javascript by applying a class with an `animation` defined when the animation should play.

### Keyframes
*Keyframes* define what an animation should look like by establishing key steps in an animation. Keyframes are given a unique name and are defined using the `@keyframes` at-rule. For example, a simple effect for the upstanding BBQ King's website:

```css
@keyframes bbq-king-takeover {
    0% {
        width: 0%;
    }
    
    75% {
        width: 40%;
    }
        
    100% {
        width: 100%;
    }
}
```
Each of the steps (`0%`, `75%`, and `100%`) is defined as a *relative* point since the duration of the animation is not specified as a part of the keyframe. The element it's applied to will grow slowly from a very small size to 40% of it's full size, then explode up to full size quickly after that. This sequence, called `bbq-king-takeover`, can now be applied to various elements using standard CSS selectors and the `animation` property.

### The animation property
Defining a keyframe won't actually change anything from our users' perspectives; in order to apply it we need to set the `animation` property on the elements we want to be animated. The `animation` property is actually shorthand for a group of other properties:

- `animation-name`: the name of the keyframe that describes the animation
- `animation-duration`: how long the animation should last, in seconds or milliseconds
- `animation-timing-function`: the rate that an animation should progress as it's running; `linear` means it'll run evenly throughout the duration while other values like `ease-in` and `ease-out` will spend more time on the beginning or end of the animation.
- `animation-delay`: how much time should pass before the animation sequence starts
- `animation-direction`: whether the animation should occur forward, backwards, or alternate between both
- `animation-iteration-count`: the number of times an animation should be played before stopping (usually 1 or infinite)
- `animation-fill-mode`: how styles should be applied before and after the animation sequence
- `animation-play-state`: whether the animation is playing or paused

If you want to apply the `bbq-king-takeover` animation to the `#promo` element when the page loads, you can do that concisely with the shorthand property:

```css
#promo {
    animation: bbq-king-takeover 3s;
}
```
This rule applies the keyframe defined above to the `#promo` element and sets the `animation-duration` to three seconds.

## The transform property
Transforms aren't specifically related to animations but often come in handy when designing them. Transforms are operations performed on elements that modify the coordinate space of the bounding box; for example, common transforms include translation, rotation, scaling, and skewing.

The `transform` property accepts transform functions as its value. Common functions include `rotate()`, `scale()`, and `translate()`.

Transforms can be combined with animations to produce pretty stunning visuals that are challenging to represent otherwise.[^1]

[^1]: ] Here's [one simple example](http://codepen.io/shayhowe/pen/Bocnt) of an `:active` transition using a translation transform to make a button "pressable." You can see another example of some stunning `transform`-driven work [on this Codepen](http://codepen.io/juliangarnier/pen/idhuG).