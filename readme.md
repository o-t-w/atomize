<p align="center"><img width="200" src="./atomize.jpg"></p>

# Atomize is a library of atomic CSS classes.

**Low specificity. Predictable styles.**

Utilities apply a single rule or a single piece of functionality. They are designed to be highly reusable.

For more information of this approach to CSS, see:

- [On the Growing Popularity of Atomic CSS
  ](https://css-tricks.com/growing-popularity-atomic-css/)
- [CSS Utility Classes and "Separation of Concerns"
  ](https://adamwathan.me/css-utility-classes-and-separation-of-concerns/)

This project is heavily inspired by [Tailwind](https://tailwindcss.com/docs/what-is-tailwind/), [Basscss](http://basscss.com/) and [Tachyons](https://tachyons.io/).

## Using Atomize

Atomize purposefully keeps things simple. There is no CLI. There are not configuration files.

You can download the files from [GitHub](https://github.com/o-t-w/atomize).
Atomize is also available on [NPM](https://www.npmjs.com/package/@pixelpusher/atomize).

The compiled CSS is also available to use from the [UNPKG CDN](https://unpkg.com/).

```
<link rel="stylesheet" href="https://unpkg.com/@pixelpusher/atomize" />
```

## Staying out of peoples way

Atomize aims to be style neutral.

- Some margin classes and grid classes are included as a reference implementation and commented out. Define your own depending on your design and use case.
- `colors.scss` is included as an _example_ of the recommended way to handle colors. Define your own depending on your design.
- Atomize does not include breakpoints. Define your own.

## Grid classes

The amount of custom layout designs that could be implemented with CSS grid are almost infinite. You can use CSS grid for everything from a small widget to the entire layout of a page. Abstracting such a large amount of options into utility classes is not feasible. Define your own classes for using CSS grid.

## At-A-Glance Understandability

Atomize avoids overly abbreviated class names and instead strives for classes that are human-readable and easily understandable.

## Escaping special characters

Atomize makes use of the `@` symbol, percentage sign, and colons (`:`) in class names.

These characters have a special meaning in CSS. These characters can be [escaped with a backslash](https://mathiasbynens.be/notes/css-escapes) to remove their special meaning.

## State Variants

To style elements on `hover`, `focus`, `active` or `focus-within`, use a `hover:`, `focus:`, `active:`, `focus-within:` prefix.

e.g. given the following classes, the button will have a pink background, while on hover it will have a blue background.

```
.bg-pink { background-color:pink; }

.hover\:bg-blue:hover { background-color: var(--blue); }
```

```
<button class="bg-pink hover:bg-blue">click</button>
```

## Handling media queries

Breakpoints should be defined as Sass variables (CSS custom properties cannot be used for this purpose).

### Breakpoint Suffixes

HTML classes that have an impact only at specific screen sizes have a `@breakpoint-name` prefix.

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

## Normalize

Atomize does not include Normalize. The vast majority of Normalize is for dealing with older browsers - particularly old versions of Internet Explorer. Atomize takes a modern approach to browser support. It does not bloat CSS with unneeded styles for obsolete long-dead browsers.

## Opinionated Styles

`base.scss` is opinionated.

It sets `box-sizing` to `border-box` for all elements rather than the browser default of `content-box`.

`base.scss` also makes working with REM units easier.

Pixel values are generally more intuitive than relative sizes (em's and rem's). However, rem values should be used to size text in order to cater for users who want to enlarge the size of text using there browser settings. Understanding the pixel value of these relative sizes is made obvious.

`1rem` is computed as `10px`. `1.6rem` is computed as `16px`. `1.7rem` is computed as `17px`. `5rem` is computed as `50px`. etc.

## Font sizes

It's important to avoid skipping heading levels when structuring your document, as it confuses screen readers. For example, after using an `<h2>` in your code, the next heading used should be either `<h2>` or `<h3>`. If you need a heading to look bigger or smaller to match a specific style, use CSS to override the default size.

Atomize applies styling directly to HTML heading elements, while also defining classes for overrides:

```
h1, .h1 {}
h2, .h2 {}
h3, .h3 {}
h4, .h4 {}
h5, .h5 {}
h6, .h6 {}
```

## Styling shadow DOM

Classes defined outside of shadow DOM don't work inside of shadow DOM. Atomize does, however, define some CSS custom properties, which _can_ be used. All colors and font sizes are defined as CSS custom properties.

## Browser support

The vast majority of classes included here work in _all browsers_. However, this library is primarily aimed towards modern everygreen browsers. New classes will be added as new CSS features emerge.

CSS features that do not work in Internet Explorer include:

- CSS custom properties
- CSS grid
- `display: contents`
- `min-content` and `max-content`
- `object-fit`
- `position: sticky`
