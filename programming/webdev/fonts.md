# Fonts

Font loading has an impact on performance:

* **Delayed text rendering:** If a web font has not loaded, browsers typically delay text rendering. [First contentful paint](performance.md#the-good-fcp-score-according-to-google) and [Largest contentful paint ](performance.md#critical-render-path)
* **Layout shifts:** The practice of font swapping has the potential to [cause layout shifts](https://web.dev/debug-layout-shifts/#identifying-the-cause-of-a-layout-shift)

**WOFF2** is an update to the original WOFF format. Developed by Google, this is considered the best format of the bunch because it offers smaller file sizes and better performance for modern browsers that support it.

### Font Loading

example of loading a font with a @font-face

```text
@font-face {
  font-family: "Open Sans";
  src: url("/fonts/OpenSans-Regular-webfont.woff2") format("woff2");
}
```

By itself, `@font-face` declaration **does not trigger font download.** Font **is downloaded** when it is used somewhere in a code:

```text
h1 {
  font-family: "Open Sans"
}
```

Other ways of loading a font are the [`preload`](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content) resource hint and the [Font Loading API](https://web.dev/optimize-webfont-loading/#the-font-loading-api).

#### Loading fonts best practices 

**Using self-hosted fonts**

If you are considering using self-hosted fonts, confirm that your site is using a [Content Delivery Network \(CDN\)](https://web.dev/content-delivery-networks/) and [HTTP/2](https://web.dev/content-delivery-networks/#http2-and-http3). Without use of these technologies, _it is much less likely that self-hosted fonts will deliver better performance_.

```text
@font-face {
    font-family: "Open Sans";
    src: url("/fonts/OpenSans-Regular-webfont.woff2") format("woff2");
    unicode-range: U+0025-00FF;
}
```

A font file will be downloaded if the page contains one or more characters matching the unicode range. `unicode-range` is commonly used to serve different font files depending on the language used by page content.

### **Font rendering**

By default, Chromium-based and Firefox browsers will block text rendering for up to 3 seconds if the associated web font has not loaded; Safari will block text rendering indefinitely.

#### **Font rendering best practices**

Use **font-display** attribute. font-display has the potential to impact **LCP**, **FCP**, and layout stability.

**`font-display`** informs the browser how it should proceed with text rendering when the associated web font has not loaded. It is defined per font-face.

```text
@font-face {
  font-family: Roboto, Sans-Serif
  src: url(/fonts/roboto.woff) format('woff'),
  font-display: swap;
}
```

strategies that will be most applicable:

* **If performance is a top priority:** Use `font-display: optional`. This is the most "**performant**" approach: text render is delayed for no longer than 100ms and there is assurance that there will be no font-swap related layout shifts.
* **If displaying text in a web font is a top priority:** Use `font-display: swap` but make sure to deliver the font early enough that it does not cause a layout shift.

sources:

* [https://web.dev/font-best-practices/](https://web.dev/font-best-practices/)

