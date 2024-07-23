# CSS

## Syntax

- Selector
- Declaration Block
- Declaration
  - Property
  - Value

## Using Stylesheets

- Inline CSS
  - styles only used on one element
- Internal CSS
  - styles only used on one page
- External CSS
  - styles used on more than one page (global)
  - usually but not always the right choice

## Selectors

### Common

- element
- class
- id

### Less Common

- attribute
- pseudo selectors
- pseudo elements

## CSS Combinators

A CSS selector can contain more than one simple selector.
Between the simple selectors, we can include a combinator.

- descendant selector (space)
- child selector (>)
- adjacent sibling selector (+)
- general sibling selector (~)

## Sizing Units

- relative (rem, %, em)
- absolute (px, pt, in)
- 1 rem = 16px by default

## Box Model

- content
- padding
- border
- margin

## Display

- inline
- block
- inline-block
  - inline but height and width are used
- flex
- grid

## Flexbox

- DevTools
- Flexbox Froggy

## CSS Grid

- eventually

## Text & Typography

- font-family
  - font stacks
  - custom fonts (ex. Google fonts)
- color = font color
- font-size
- line-height
- font-weight

## Colors

- HEX (old and reliable)
- RGB (newer, supports more colors)
- HSL (newest, may not be supported in all browsers)
- use strong brand colors to highlight or accent your design but don't overuse them (for example as a background for entire app)
- design a site in grayscale (a range of gray shades from white to black), then add brand colors at the end
- maintain high contrast

## Specificity

A numerical ranking of selectors.

- Diagrams
  - SpeciFISHity (not a typo)
- Devtools

## The Cascade

1. inline
2. internal
3. external
4. browser
5. specificity
6. if specificity same, lower in the file wins

## Exercise 1

- style `header` to match design
- style `nav` to match design
