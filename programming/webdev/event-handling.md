# Event handling

All events begin at the window and first go through the capturing phase. This means that when an event is dispatched, it starts the window and travels "downwards" towards its target element _first_.

```text
<html>
  <body>
    <div id="A">
      <div id="B">
        <div id="C"></div>
      </div>
    </div>
  </body>
</html>
```

```text
document.getElementById('C').addEventListener(
  'click',
  function (e) {
    console.log('#C was clicked');
  },
  true,
);
```

### Event capturing

Click on \#C  an event, originating at the `window`, is dispatched. 

`window` =&gt; `document` =&gt; `<html>` =&gt; `<body>` =&gt; ... =&gt;  **target**

**The click vent** _**propagate**_ **from the window to its target element \(\#C\) by way of every element between the `window` and `#C`**

Click event starts from window and goes through the DOM with following process:

* Is anything listening for a click event on the `window` in the capturing phase? - **NO** -&gt; move to next element = **document**
* Is anything listening for a click event on the `document` in the capturing phase?" - **NO** -&gt; move to the next element = &lt;html&gt; and so on
* until its meet the element which is in capturing phase in our case element with id = \#C
* Is anything listening for a click event on the `#C` in the capturing phase? - **YES -&gt;** This brief period of time when the event is _**at**_ **the target,** is known as the "**target phase**." At this point, the event handler will fire, the browser will console.log "\#C was clicked"._Wrong!_ The process continues, but now it changes to the bubbling phase.
* Next the bubbling phase starts

### Event bubbling

The browser asks:

* Is anything listening for a click event on `#C` in the **bubbling** **phase**? It is possible to listen for an event in both phases **bubbling** and **capturing** . if there are two `.addEventListener()` , one with `capture = true` and another with `capture = false` **both events will fire but in different  phases.**
* Event will **propagate** \("bubble"\) to the  parent element `#B` **,** Is anything listening for click events on `#B` in the bubbling phase? -&gt; No, no handers here.
* Event bubble to the next parent element and so on and so on till the `window` 
* Is anything listening for click events on the `window` in the bubbling phase?

### event.stopPropagation\(\)

if you call `stopPropagation()` anywhere in the **capturing phase**, the event will never make it to the target phase or **bubbling phase**. 

If you call it in the **bubbling phase,** it will have already gone through the capturing phase, but it will cease "bubbling up" from the point at which you called it.

### event.stopImmediatePropagation\(\)

Similar to `stopPropagation`, but rather than stopping an event from traveling to descendents \(capturing\) or ancestors \(bubbling\), this method only applies when you have more than one event handler wired up to a single element.

It is possible to have multiple event handlers on one element. In this case they will fire in an order how they were wired up. Calling `stopImmediatePropagation()` prevents firing next event handlers.

**example**: [event.stopImmediatePropagation\(\)](https://web.dev/eventing-deepdive/#event.stopimmediatepropagation%28%29)

### event.preventDefault\(\)

Preventing the default action to fire, for instance it prevents redirection for anchor click.

sources**:**

* [JavaScript eventing deep dive](https://web.dev/eventing-deepdive/)

