# Top 10 a11y issues

This is a rough list of the most common accessibility (a11y) errors we found while building FT.com. This list is referenced in LINK TO SLIDES


## Colour contrast

`• This element has insufficient contrast at this conformance level. Expected a contrast ratio of at least 4.5:1, but text in this element has a contrast ratio of 4.4:1. Recommendation: change text colour to #6560fd.`

By far the most popular [pa11y-ci](https://github.com/pa11y/ci) error we had when cleaning up FT.com for accessibility. It tells you that a piece of text will be hard to read.

More specifically, it's telling you that the colour contrast ratio between that text and the background under it falls below a ratio of 4.5:1 (for WCAG2.0AA). It will also recommend a colour with good enough contrast you can use. If that's not suitable, you can choose your own colour and check it with the [WebAIM Contrast Checker](webaim.org/resources/contrastchecker/)

### What if the item is visually hidden?

We often get the above error for items that are visually hidden (due to accessibility or otherwise). If an item is hidden or set off-screen with a css class, `pa11y` usually can't tell, and will fail if contrast doesn't pass.

One option would be to tell `pa11y` (via [config](https://github.com/pa11y/pa11y#hideelements-string)) to ignore all elements with a certain class: if `visually-hidden` don't even check it. The problem for us in this case is that most visually hidden elements contain elements we want to make available to screen readers, like additional explanatory text, such as:

```html
<a href="foo.html" target="_blank">Foo<span class="visually-hidden"> opens in a new window</span></a>
```

While this is a simple example, in more complex cases we really want to make sure `pa11y` is running on the hidden content, which is specifically being served to assistive tech users, so ignoring the `visually-hidden` class altogether was not an option for us.

Ultimately, we just make sure all color contrast passes, whether visible or not. This also ensures that if, for whatever reason, that `visually-hidden` class is eventually removed from that element it will continue to pass `pa11y` and not break our builds.

## When to "alt" an image?

`• Error: Img element missing an alt attribute. Use the alt attribute to specify a short text alternative.`

The `alt` attribute. Literally there as an alternative to the image when, for whatever reason, it cannot be seen (i.e. the link is broken, the network is slow, you're a screen reader user, etc.)

The quick solution is to add some text to the `alt` attribute. While it will make `pa11y` pass (because `pa11y` can't know the purpose of the image, or how it fits in your context) it's not always the right solution.

### Decorative Images

When images don't add anything to the context and their only role is decoration the recommendation is to use a "null alt" or `alt=""`. This will pass `pa11y` and compiles with WCAG2.0. However, some screen readers like VoiceOver may still pick up the image and read out `image` to the user. To avoid this we add `role="presentation"` for the image to be ignored altogether.

<img alt="" role="presentation" src="https://cloud.githubusercontent.com/assets/3425322/25666914/cdd6ce28-3019-11e7-9293-82a439910ad8.png" width="300px">

### Simple images with information

When the image does convey information easily described in one line, we use the `alt` attribute, i.e.
```html
<img src="..." alt="Hilary 57%, Trump 34%, Would not vote 9%">
```
<img alt ="Hilary 57%, Trump 34%, Would not vote 9%" src="https://media.licdn.com/mpr/mpr/shrinknp_800_800/AAEAAQAAAAAAAAS9AAAAJDFmYTU5ZDQ4LWRlZDAtNDJjYi1hNDA0LTIwYmQ5NzZhZTBiZg.jpg" width="300">

### Complex Infographics and charts 🏗

We are actively working on a solution for our more complex images like infographics. One recommendation is to use attribute `longdesc` but support for it is poor and is currently deprecated, so we will not be going down this route. Cramming a long description inside the `alt`? Not ideal (maybe?). The solution that seems most appealing is to add a long description either visually hidden or in a visibly linked, separate document (better).

Watch this space for updates...

<img src="https://www.ft.com/__origami/service/image/v2/images/raw/http%3A%2F%2Fcom.ft.imagepublish.prod.s3.amazonaws.com%2F74c40692-fe97-11e6-96f8-3700c5664d30?source=next&fit=scale-down&width=300">

## Duplicate links
read more
read more

## Image links

## Don't burn "title" with 🔥 just yet


## Required form fields
