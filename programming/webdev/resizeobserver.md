# ResizeObserver

Reacts to changes is size of any of the observed elements, independent of what causes the change, provides an access to the new size of the observed elements.

```text
const resizeObserver = new ResizeObserver(entries => {
    for(let entry of entries) {
        cons contentRect = entry.contentRect;
        console.log('Element:', entry.target);
        console.log(`Element size: ${cr.width}px x ${cr.height}px`);
        console.log(`Element padding: ${cr.top}px ; ${cr.left}px`);
    }
});

// Observe one or multiple elements
ro.observe(someElement);
```

Generally, a [`ResizeObserverEntry`](https://developer.mozilla.org/docs/Web/API/ResizeObserverEntry) reports the content box of an element through a property called `contentRect`, which returns a [`DOMRectReadOnly`](https://developer.mozilla.org/docs/Web/API/DOMRectReadOnly) object. The content box is the box in which content can be placed. It is the border box minus the padding.

sorces:

* [MDN ResizeObserver](https://developer.mozilla.org/en-US/docs/Web/API/ResizeObserver)
* [Google web.dev ResizeObserver](https://web.dev/resize-observer/)

