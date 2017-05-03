# Top 10 a11y issues

This is a rough list of the most common accessibility (a11y) errors we found while building FT.com. This list is referenced in LINK TO SLIDES


## Color contrast

`• Error: This element has insufficient contrast at this conformance level. Expected a contrast ratio of at least 4.5:1, but text in this element has a contrast ratio of 1.03:1. Recommendation: change text colour to #6a7979.`

By far the most popular [pa11y-ci](https://github.com/pa11y/ci) error we had when cleaning up FT.com for accessibility. It tells you that a piece of text will be hard to read.

More specifically, it's telling you that the color contrast ratio between that text and the background under it falls below a ratio of 4.5:1 (for WCAG2.0AA). It will also recommend a color with good enough contrast you can use. If that's not suitable, you can choose your own colour and check it with the [WebAIM Contrast Checker](webaim.org/resources/contrastchecker/)

### What if the item is visually hidden?

## When to "alt" an image?
The `alt` attribute. Literally there as an alternative to the image when, for whatever reason, it cannot be seen (i.e. the link is broken, the network is slow, you're a screen reader user, etc.)



### Decorative Images

### Simple images with information

### Complex Infographics and charts 🏗

## Duplicate links
read more
read more

## Image links

## Don't burn "title" with 🔥 just yet


## Required form fields
