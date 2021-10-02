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

Click on \#C  an event, originating at the `window`, is dispatched. 

`window` =&gt; `document` =&gt; `<html>` =&gt; `<body>` =&gt; ... =&gt;  **target**

**The click vent** _**propagate**_ **from the window to its target element \(\#C\) by way of every element between the `window` and `#C`**

Click event starts from window and goes through the DOM with following process:

* Is anything listening for a click event on the `window` in the capturing phase? - **NO** -&gt; move to next element = **document**
* Is anything listening for a click event on the `document` in the capturing phase?" - **NO** -&gt; move to the next element = &lt;html&gt; and so on
* until its meet the element which is in capturing phase in our case element with id = \#C
* Is anything listening for a click event on the `#C` in the capturing phase? - **YES -&gt;** This brief period of time when the event is _**at**_ **the target,** is known as the "**target phase**." At this point, the event handler will fire, the browser will console.log "\#C was clicked"._Wrong!_ The process continues, but now it changes to the bubbling phase.  ****

sources**:** 

* \*\*\*\*[**https://web.dev/eventing-deepdive/**](https://web.dev/eventing-deepdive/)\*\*\*\*

