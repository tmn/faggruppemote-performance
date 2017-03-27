# Web Performance

Testing performance using Chrome DevTools

## Analyzing network performance

Analyzing your network performance to find blocking scripts and large resources.

[Chrome Network sample 1](https://googlechrome.github.io/devtools-samples/network/gs/v1.html)

[Chrome Network sample 2](https://googlechrome.github.io/devtools-samples/network/gs/v2.html)


## Style calculation and CSS performance

__Style__ > __Layout__ > __Paint__ > __Composite__

__STYLE__

> the process of figuring out which CSS rules apply to which element

__LAYOUT__

> the browsers begins calculating how much space an element takes up on screen

__PAINT__

> this is the process of filling in the pixels. They are often layered

__COMPOSITE__
> draws the pixels/layers on screen

[CSS Triggers](https://csstriggers.com)

### Selectors

> Roughly 50% of the time used to calculate the computed style for an element is used to match selectors, and the other half of the time is used for constructing the RenderStyle (computed style representation) from the matched rules.

Rune Lillesveen, Opera / [Style Invalidation in Blink](https://docs.google.com/document/d/1vEW86DaeVs4uQzNFI5R-_xS9TcS1Cs_EUsHRSgCHGu8/view)


### Selector complexity

Just a simple selector:

```css
.button {
  /* styles */
}
```

Let's say you want to get the minus nth child + 1 element inside a control group in a list of articles (aka. the last button element)

```css
article.controls:nth-last-child(-n+1) .button {
  /* styles */
}
```

But all you want to do is:

```css
.final-article-control-button {
  /* styles */
}
```

### Number of elements being styled

Reduce the number of elements being styled.

* be more specific

Might not be an issue in modern browsers. I.e. some modern browsers doesn't need to recalculate its computed styles on its children.


### Critical rendering path

![CRP](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/images/progressive-rendering.png)

### Avoid Large, Complex Layouts and Layout Thrashing

Performance

> * Avoid setTimeout or setInterval for visual updates; always use requestAnimationFrame instead.
> * Move long-running JavaScript off the main thread to Web Workers.
> * Use micro-tasks to make DOM changes over several frames.
> * Use Chrome DevTools’ Timeline and JavaScript Profiler to assess the impact of JavaScript.

and layouts

> * Layout is normally scoped to the whole document.
> * The number of DOM elements will affect performance; you should avoid triggering layout wherever possible.
> * Assess layout model performance; new Flexbox is typically faster than older Flexbox or float-based layout models.
> * Avoid forced synchronous layouts and layout thrashing; read style values then make style changes.
