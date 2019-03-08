# Oppenheimer is a library of atomic CSS classes.

Utilities apply a single rule or a single piece of functionality. They are designed to be highly reusable.

For more information of this approach to CSS, see:

- [On the Growing Popularity of Atomic CSS
  ](https://css-tricks.com/growing-popularity-atomic-css/)
- [CSS Utility Classes and "Separation of Concerns"
  ](https://adamwathan.me/css-utility-classes-and-separation-of-concerns/)

## Staying out of peoples way

Oppenheimer leaves it to the user to define colors and breakpoints, etc. See below for the _recommended_ way of handling breakpoints.

`color.scss` is included purely as an _example_ of the recommended way to apply colors. 

## Handling media queries

### Breakpoint Suffixes

HTML classes that have an impact only at specific screen sizes have a `@breakpoint-name` prefix.

The following characters have a special meaning in CSS: !, ", #, \$, %, &, ', (, ), \*, +, ,, -, ., /, :, ;, <, =, >, ?, @, [, \, ], ^, `, {, |, }, and ~.

These characters can be [escaped with a backslash](https://mathiasbynens.be/notes/css-escapes) to remove its special meaning.

e.g.:

```
.font-xl {
  font-size: 75px;
}

@media (max-width: $breakpoint-mobile) {
  .\@sm\:font-l {
    font-size: 50px;
  }
}
```

Given the following markup, a `h1` would be 50 pixels on mobile and 75 pixels on all larger screens.

```
<h1 class="font-xl @sm:font-l">Lorem Ipsum Heading</h1>
```

## Opinionated Styles

`base.scss` is highly opinionated.

It sets `box-sizing` to `border-box` for all elements rather than the browser default of `content-box`.

It also makes working with REM units easier.

Pixel values are generally more intuitive than relative sizes (em's and rem's). However, rem values should be used to size text in order to cater for users who want to enlarge the size of text using there browser settings. Understanding the pixel value of these relative sizes is made obvious.

`1rem` is computed as `10px`. `1.6rem` is computed as `16px`. `1.7rem` is computed as `17px`. `5rem` is computed as `50px`. etc.
