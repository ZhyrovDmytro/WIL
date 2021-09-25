# Performance

[Long read from google](https://web.dev/fast/#optimize-your-javascript)

Metrics that have an impact on web page speed score \(0-100\):

* First Contentful Paint
* First Meaningful Paint
* Speed Index
* First CPU Idle
* Time to Interactive
* Max Potential First Input Delay

User has 2 steps while the page is rendering:

1. Partially interaction with the page \(**FMP** - First meaningful paint\)
2. Full interaction with the page \(**TTI** - Time to interactive\)

**FMP** -  HTML is loaded, text is loaded. User can read content without interaction.

**TTI** - web page is ready for use, scripts are loaded.

~~**FMP** one of the main metrics which describes **Critical render path.**~~

In early 2019, Google announced that they would **evaluate a website’s speed ranking** by focusing on two performance metrics: **First Contentful Paint \(FCP\)** and **First Input Delay \(FID\)**.

### Critical render path

**Critical render path -** set of actions and resources that browser should perform, download and process in order for the user to get their first workable result. \(load HTML, CSS\).

1. Request HTML
2. Receive an HTML
3. Parse the HTML
4. Build a DOM tree
5. Request for CSS
6. Receive CSS
7. Build CSS tree
8. Run JS code
9. Rebuild DOM if needed
10. Build render tree
11. Paint the page \(layout -&gt; paint -&gt; Composite

**FCP** \(first contentful paint\) -  measures how users perceive the performance of a website, rather than what a speed test tool measures.

FCP requires some content to be rendered for instance text, images, non-white &lt;canvas/&gt;.

![First Contentful Paint in GTMetrix&#x2019;s Timings tab](../../.gitbook/assets/image%20%282%29%20%281%29.png)

### The good FCP score according to Google.

[FCP should occur within 1.8 seconds or less](https://web.dev/fcp/#what-is-a-good-fcp-score). If site FCP takes 3+ seconds, it’s considered slow.

**LCP is primarily affected by four factors:**

* Slow server response times
* Render-blocking JavaScript and CSS
* Resource load times
* Client-side rendering

### How to improve 

#### 1. Reduce Server Response Time \(TTFB - time to first byte\)

FCT highly depended on TTFB, ways to reduce TTFB:

1. **Use a Quality CDN**\(helps delivering static resources like images, videos, scripts\)
2. **Enable Caching** Caching helps with reducing TTFB by decreasing the server processing time

### 2. Remove Render-Blocking Resources

1. **Inline critical Resources**. Identify JS and CSS that are needed for FCP of the webpage,  [**guide by Google on how to identify critical resources**](https://web.dev/render-blocking-resources/#how-to-identify-critical-resources). Remove them from the render-blocking resource and then inline them inside your HTML page with **&lt;script&gt;** and **&lt;style&gt;** tags
2. **Defer Non-Critical Resources.** Mark non-critical res. with [**async/defer** attr](https://javascript.info/script-async-defer)

### 3. Generate Critical Path CSS and inline it

If load CSS asynchronously the browser would show unstyled content to the user before CSS is loaded. This is known as [Flash of Unstyled Content \(FOUC\)](https://en.wikipedia.org/wiki/Flash_of_unstyled_content) 

Use free online tools like [Pegasaas](https://pegasaas.com/critical-path-css-generator/) to generate Critical Path CSS. It works perfectly for most use cases. Check out Google’s [Analyzing Critical Rendering Path Performance](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp) for more.

Once you’ve generated the Critical Path CSS, you need to inline it inside the HTML document.

### 3. Optimize the DOM size

* lazyload HTML
* paginate comments, posts, products
* limit number of posts
* don't hide unwanted elements with CSS, just not render them

### 4. Resource hints

When a user visits a website, the browser requests the HTML document from the server, parses it, submits separate requests for any other referenced resources, and after loading and parsing them all, renders the web page.

#### **DNS Prefetching**

Adding the **dns-prefetch** parameter will tell the browser to resolve the DNS of the URL as quickly as possible. 

```text
<link rel="dns-prefetch" href="//external-website.com">
```

Preconnect works much like DNS prefetching, except it doesn’t stop at just resolving the DNS. It’ll also go ahead and establish the TCP handshake and TLS negotiation \(if any\).

```text
<link rel="preconnect" href="https://example.com">
```

Bear in mind that preconnect can take up valuable processing time, especially for secure connections.

#### **Prefetch**

If you’re certain that a resource will be used in the future, then you can suggest the browser to **prefetch** it right away and store it in the browser. Unlike DNS prefetching, here you’re telling the browser to start loading the resource immediately.   


```text
<link rel="prefetch" href="scripts.js">
```

#### **Prerender**

This is the most powerful resource hint. Adding the **prerender** parameter to a resource forces the browser to load all its assets, parse them, create a DOM tree, apply styles, execute scripts, render the webpage, and keep it ready to be served. If you visit the URL mentioned in the **href** later, the page will be loaded instantly.

```text
<link rel="prerender" href="https://example.com/next-page">
```

#### **Preload**

Unlike prefetching, which acts more like a suggestion to the browser, the **preload** resource hint directs the browser to load the assets regardless of what it thinks. The browser cannot ignore the preloading directive.

```text
<head>
  ...
  <link rel="preload" href="styles.css" as="style">
  <link rel="preload" href="ui.js" as="script">
  ...
</head>
```

The earlier the browser starts to request the declared preload links, the faster your pages can load.

Resource hints won’t help much when a user visits your website for the first time. But every subsequent page they visit will render significantly faster. Since Google uses real usage data to evaluate a website’s speed ranking, resource _hints will help improve your site’s **FCP**_.

### 5. Minify blocking JS and CSS

#### Reduce CSS blocking time <a id="reduce-css-blocking-time"></a>

* Minify CSS
* Defer non-critical CSS
* Inline critical CSS

Plugins to minify CSS for builder tools:

* For webpack: [optimize-css-assets-webpack-plugin](https://github.com/NMFR/optimize-css-assets-webpack-plugin)
* For Gulp: [gulp-clean-css](https://www.npmjs.com/package/gulp-clean-css)
* For Rollup: [rollup-plugin-css-porter](https://www.npmjs.com/package/rollup-plugin-css-porter)

#### Reduce JavaScript blocking time <a id="reduce-javascript-blocking-time"></a>

* [Minify and compress JavaScript files](https://web.dev/reduce-network-payloads-using-text-compression/)
* [Defer unused JavaScript](https://web.dev/reduce-javascript-payloads-with-code-splitting/)
* [Minimize unused polyfills](https://web.dev/serve-modern-code-to-modern-browsers/)

[Reduce JavaScript blocking time](https://web.dev/optimize-lcp/#reduce-javascript-blocking-time) section to read more about these optimizations.  


#### Use server-side rendering

Use the server to render the application into HTML, where the client then "[hydrates](https://www.gatsbyjs.org/docs/react-hydration/)" all the JavaScript and required data onto the same DOM content. This can improve LCP by ensuring the main content of the page is first rendered on the server rather than only on the client, but there are a **few drawbacks**:

* Maintaining the same JavaScript-rendered application on the server and the client can increase complexity.
* Executing JavaScript to render an HTML file on the server will always increase server response times \(TTFB\) as compared to just serving static pages from the server.
* A server-rendered page may look like it can be interacted with, but it can't respond to any user input until all the client-side JavaScript has executed. In short, it can make [**Time to Interactive**](https://web.dev/tti/) \(TTI\) worse.

**Dive into different server-rendering architectures, here -&gt;** [**Rendering on the web**](https://developers.google.com/web/updates/2019/02/rendering-on-the-web)**.**

#### Use pre-rendering <a id="use-pre-rendering"></a>

Pre-rendering is a **separate technique that is less complex than server-side rendering** and also provides a way to improve LCP in your application. A headless browser, which is a browser without a user interface, is used to generate static HTML files of every route during build time. These files can then be shipped along with the JavaScript bundles that are needed for the application.



