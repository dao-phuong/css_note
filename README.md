# CSS Note
Some note that I think it's important about CSS

## Ways to override Style
  ### 1. Declare order
  The order of the class declarations in the <style> section are what is important. The second declaration will always take precedence over the first. 
  
    *Note: It doesn't matter which order the classes are listed in the HTML element.*
```
    <style>
      .pink-text {
        color: pink;
      }
      .blue-text {
        color: blue;      // this style take precedence
      }
    </style>
  <h3 class="pink-text blue-text">Hello World!</h3>
``` 
  ### 2. Id selector
    Id declarations override class declarations, regardless of where they are declared in your style element CSS.
 
```
    <style>
      .pink-text {
        color: pink;
      }
      .blue-text {
        color: blue;
      }
      #orange-text {
        color: orange;      // this style take precedence
      }
    </style>
    <h3 id="orange-text" class="pink-text blue-text">Hello World!</h3>
```
  ### 3. Inline style
   In-line styles will override all the CSS declarations in your style element.
   
```
   <style>
      .pink-text {
        color: pink;
      }
      .blue-text {
        color: blue;
      }
      #orange-text {
        color: orange;
      }
  </style>
  <h3 id="orange-text" class="pink-text blue-text" style="color: white">Hello World!</h3> // this inline style take precedence
```
   ### 4. Using Important
    When you absolutely need to be sure that an element has specific CSS, you can use !important
    
```
    <style>
      .pink-text {
        color: pink !important;      // this style take precedence
      }
      .blue-text {
        color: blue;
      }
      #orange-text {
        color: orange;
      }
    </style>
    <h3 id="orange-text" class="pink-text blue-text" style="color: white">Hello World!</h3>
```

## CSS attribute notes
- Overflow only works on block level elements.
- Vertical align only works for inline,inline-blocks,images,and table elements.

## Design Guidelines

1. Structure layout first
2. Use more padding
3. Use more line height on body than headings
4. Do not use pure black
5. Use fewer fonts, or be consistent with fonts
6. Use fewer colors, or complimentary colors
7. Be consistent with borders and corners
8. Fine details, transitions and animations last
9. Don’t go overboard with drop shadows, gradients, or animations

## EM and REM unit
### EM unit is parent-child relationship unit
```
<!DOCTYPE html>
<html>
    <head>
        …
        <style>
.wrapper { font-size: 20px; }
.a { font-size: 1.5em; }
.b { font-size: 2.0em; }
        </style>
    </head>
    <body>
        <div class="wrapper">
            <span class="a">hello from inside .a</span>
            <span class="b">hello from inside .b</span>
        </div>
    </body>
</html>
```
The result we have is: .a is 30px an .b is 40px

### REM unit is root-child relationship unit
```
   html <- root
   /  \
head  body
 /      \
…        …
```
Let's see example below
```
<!DOCTYPE html>
<html>
    <head>
        …
        <style>
:root {
  font-size: 15px;
}
.wrapper { font-size: 20px; }
.a { font-size: 1.5rem; }
.b { font-size: 2.0rem; }
        </style>
    </head>
    <body>
        <div class="wrapper">
            <span class="a">hello from inside .a</span>
            <span class="b">hello from inside .b</span>
        </div>
    </body>
</html>
```
So, the result we have will be: .a is 22.5px and .b is 30px

## Flexbox

### Style apply for the container (flex container)

#### justify-content: Align items horozontally (when flex-direction is column, justify-content change to vertical)
Accept following values:
- flex-start: items align to left side of container
- flex-end: items align to right side of container
- center: items align at the center of container
- space-between: Items display with equal spacing between them.
- space-around: Items display with equal spacing around them.

#### align-items: Align items vertically (when flex-direction is column, align-item change to horizontal)
Accept following values:
- flex-start: Items align to the top of the container.
- flex-end: Items align to the bottom of the container.
- center: Items align at the vertical center of the container.
- baseline: Items display at the baseline of the container.
- stretch: Items are stretched to fit the container.

#### flex-direction: define the direction items are placed in the container
Accept following values:
- row: Items are placed the same as the text direction
- row-reverse: Items are placed opposite tho the text direction
- column: Items are placed top to bottom
- column-reverse: Items are placed bottom to top

### flex-wrap: define how items wrap or not
Accept values:
- nowrap: Every item is fit to a single line.
- wrap: Items wrap around to additional lines.
- wrap-reverse: Items wrap around to additional lines in reverse.

### flex-flow: shorthand property using to combine flex-direction and flex-wrap

### align-content: set how multiple lines are spaced apart from each other.
Accept values:
- flex-start: Lines are packed at the top of the container
- flex-end: Lines are packed at the bottom of the container
- center: Lines are packed at the vertical center of the container
- space-between: Lines display with equal spacing between them
- space-around: Lines display with equal spacing around them
- stretch: Lines are stretched to fit the container

**When there is only one line, align-content has no effect**

### Style apply for the items (flex items)

#### order: Using to reorder item in flexbox
Its value can be positive or negative. Default is 0 (current position)

#### align-self: accept the same values as align-items and its value for the specific item.

## ::before and ::after
These pseudo-elements are used to add something before or after a selected element. 
For the ::before and ::after pseudo-elements to function properly, they must have a defined content property. This property is usually used to add things like a photo or text to the selected element. When the ::before and ::after pseudo-elements are used to make shapes, the content property is still required, but it's set to an empty string.


## Applied Accessibility
CSS's magic can also improve accessibility on your page when you want to visually hide content meant only for screen readers. This happens when information is in a visual format (like a chart), but screen reader users need an alternative presentation (like a table) to access the data. CSS is used to position the screen reader-only elements off the visual area of the browser window.

Here's an example of the CSS rules that accomplish this:
```
.sr-only {
  position: absolute;
  left: -10000px;
  width: 1px;
  height: 1px;
  top: auto;
  overflow: hidden;
}
```

Note
The following CSS approaches will NOT do the same thing:
- `display: none;` or `visibility: hidden;` hides content for everyone, including screen reader users
- Zero values for pixel sizes, such as `width: 0px; height: 0px;` removes that element from the flow of your document, meaning screen readers will ignore it

### Improve Readability with High Contrast Text
Low contrast between the foreground and background colors can make text difficult to read. Sufficient contrast improves the readability of your content, but what exactly does "sufficient" mean?

The Web Content Accessibility Guidelines (WCAG) recommend at least a 4.5 to 1 contrast ratio for normal text. The ratio is calculated by comparing the relative luminance values of two colors. This ranges from 1:1 for the same color, or no contrast, to 21:1 for white against black, the strongest contrast. There are many contrast checking tools available online that calculate this ratio for you.


### Avoid Colorblindness Issues by Using Sufficient Contrast
Color is a large part of visual design, but its use introduces two accessibility issues. First, color alone should not be used as the only way to convey important information because screen reader users won't see it. Second, foreground and background colors need sufficient contrast so colorblind users can distinguish them.

Colorblind users have trouble distinguishing some colors from others - usually in hue but sometimes lightness as well. You may recall the contrast ratio is calculated using the relative luminance (or lightness) values of the foreground and background colors.

In practice, the 4.5:1 ratio can be reached by darkening the darker color and lightening the lighter one with the aid of a color contrast checker. Darker colors on the color wheel are considered to be blues, violets, magentas, and reds, whereas lighter colors are oranges, yellows, greens, and blue-greens.

### Give Links Meaning by Using Descriptive Link Text
Screen reader users have different options for what type of content their device reads. This includes skipping to (or over) landmark elements, jumping to the main content, or getting a page summary from the headings. Another option is to only hear the links available on a page.

Screen readers do this by reading the link text, or what's between the anchor (a) tags. Having a list of "click here" or "read more" links isn't helpful. Instead, you should use brief but descriptive text within the a tags to provide more meaning for these users.

### Make Links Navigatable with HTML Access Keys
HTML offers the `accesskey` attribute to specify a shortcut key to activate or bring focus to an element. This can make navigation more efficient for keyboard-only users

HTML5 allows this attribute to be used on any element, but it's particularly useful when it's used with interactive ones. This includes links, buttons, and form controls.

Here's an example:
```
<button accesskey="b">Important Button</button>
```

### Use tabindex to Add Keyboard Focus to an Element
The HTML `tabindex` attribute has three distinct functions relating to an element's keyboard focus. When it's on a tag, it indicates that element can be focused on. The value (an integer that's positive, negative, or zero) determines the behavior.

Certain elements, such as links and form controls, automatically receive keyboard focus when a user tabs through a page. It's in the same order as the elements come in the HTML source markup. This same functionality can be given to other elements, such as `div`, `span`, and `p`, by placing a `tabindex="0"` attribute on them. Here's an example:

```
<div tabindex="0">I need keyboard focus!</div>
```

Note
A negative `tabindex` value (typically -1) indicates that an element is focusable, but is not reachable by the keyboard. This method is generally used to bring focus to content programmatically (like when a `div` used for a pop-up window is activated).

*Bonus - using `tabindex` to `p` also enables the CSS pseudo-class `:focus` to work on the `p` tag.*

### Use tabindex to Specify the Order of Keyboard Focus for Several Elements
The `tabindex` attribute also specifies the exact tab order of elements. This is achieved when the value of the attribute is set to a positive number of 1 or higher.

Setting a `tabindex="1"` will bring keyboard focus to that element first. Then it cycles through the sequence of specified `tabindex` values (2, 3, etc.), before moving to default and `tabindex="0"` items.

It's important to note that when the tab order is set this way, it overrides the default order (which uses the HTML source). This may confuse users who are expecting to start navigation from the top of the page. This technique may be necessary in some circumstances, but in terms of accessibility, take care before applying it.

Here's an example:
```
<div tabindex="1">I get keyboard focus, and I get it first!</div>

<div tabindex="2">I get keyboard focus, and I get it second!</div>
```

# Colors
**Using different combinations of colors can really change the look of a website, and a lot of thought can go into picking a color palette that works with your content**
The color wheel is a useful tool to visualize how colors relate to each other - it's a circle where similar hues are neighbors and different hues are farther apart. When two colors are opposite each other on the wheel, they are called complementary colors. They have the characteristic that if they are combined, they "cancel" each other out and create a gray color. However, when placed side-by-side, these colors appear more vibrant and produce a strong visual contrast.

Link of color wheel tool: https://www.sessions.edu/color-calculator/

Some examples of complementary colors with their hex codes are:
```
red (#FF0000) and cyan (#00FFFF)
green (#00FF00) and magenta (#FF00FF)
blue (#0000FF) and yellow (#FFFF00)
```

Computer monitors and device screens create different colors by combining amounts of red, green, and blue light. This is known as the RGB additive color model in modern color theory. Red (R), green (G), and blue (B) are called primary colors. Mixing two primary colors creates the secondary colors cyan (G + B), magenta (R + B) and yellow (R + G). You saw these colors in the Complementary Colors challenge. These secondary colors happen to be the complement to the primary color not used in their creation, and are opposite to that primary color on the color wheel. For example, magenta is made with red and blue, and is the complement to green.

Tertiary colors are the result of combining a primary color with one of its secondary color neighbors. For example, red (primary) and yellow (secondary) make orange. This adds six more colors to a simple color wheel for a total of twelve.

There are various methods of selecting different colors that result in a harmonious combination in design. One example that can use tertiary colors is called the split-complementary color scheme. This scheme starts with a base color, then pairs it with the two colors that are adjacent to its complement. The three colors provide strong visual contrast in a design, but are more subtle than using two complementary colors.

Here are three colors created using the split-complement scheme:

|Color|	Hex |
| ----------- | ----------- | 
|orange	|#FF7D00|
|cyan	|#00FFFF|
|raspberry|#FF007D|

# Responsive

## Make an Image Responsive
Making images responsive with CSS is actually very simple. Instead of applying an absolute width to an element:
```
img { width: 720px; }
```

You can use:
```
img {
  max-width: 100%;
  display: block;
  height: auto;
}
```
The `max-width` property of 100% scales the image to fit the width of its container, but the image won't stretch wider than its original width. Setting the `display` property to `block` changes the image from an `inline` element (its default), to a `block` element on its own line. The `height` property of auto keeps the original aspect ratio of the image.

## Use a Retina Image for Higher Resolution Displays
The simplest way to make your images appear "retina" (and optimize them for retina displays) is to define their width and height values as only half of what the original file is.
Here is an example of an image that is only using half of the original height and width:
```
<style>
  img { height: 250px; width: 250px; }
</style>
<img src="coolPic500x500" alt="A most excellent picture">
```

## Make Typography Responsive
Instead of using em or px to size text, you can use viewport units for responsive typography. Viewport units, like percentages, are relative units, but they are based off different items. Viewport units are relative to the viewport dimensions (width or height) of a device, and percentages are relative to the size of the parent container element.

The four different viewport units are:
- `vw: 10vw` would be 10% of the viewport's width.
- `vh: 3vh` would be 3% of the viewport's height.
- `vmin: 70vmin` would be 70% of the viewport's smaller dimension (height vs. width).
- `vmax: 100vmax` would be 100% of the viewport's bigger dimension (height vs. width).
