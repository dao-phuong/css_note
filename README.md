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

**When there is only one line, align-content has no effect

### Style apply for the items (flex items)

#### order: Using to reorder item in flexbox
Its value can be positive or negative. Default is 0 (current position)

#### align-self: accept the same values as align-items and its value for the specific item.



