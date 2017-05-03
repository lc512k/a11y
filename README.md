# Top 10 a11y issues

This is a rough list of the most common accessibility (a11y) errors we found while building FT.com. This list is referenced in LINK TO SLIDES


## Colour contrast

`• This element has insufficient contrast at this conformance level. Expected a contrast ratio of at least 4.5:1, but text in this element has a contrast ratio of 4.4:1. Recommendation: change text colour to #6560fd.`

By far the most popular [pa11y-ci](https://github.com/pa11y/ci) error we had when cleaning up FT.com for accessibility. It tells you that a piece of text will be hard to read.

More specifically, it's telling you that the colour contrast ratio between that text and the background under it falls below a ratio of 4.5:1 (for WCAG2.0AA). It will also recommend a colour with good enough contrast you can use. If that's not suitable, you can choose your own colour and check it with the [WebAIM Contrast Checker](webaim.org/resources/contrastchecker/)

This is an example of the color pa11y complained about (`bad-contrast`) and the color it recommended instead (`good-contrast`). Nearly identical, right?

![bad vs good contrast](https://cloud.githubusercontent.com/assets/3425322/25665813/99989bd0-3016-11e7-921e-37d32146698b.png)

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
