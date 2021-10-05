# Service Worker

Is a script that your browser runs in the background, separate from a web page, allows you to support offline experiences, giving developers complete control over the experience.. Already include features like [push notifications](https://developers.google.com/web/updates/2015/03/push-notifications-on-the-open-web) and [background sync](https://developers.google.com/web/updates/2015/12/background-sync). In the future, service workers might support other things like periodic sync or geofencing.

* Can't access DOM directly, can communicate with the pages it controls by responding to messages sent via the [postMessage](https://html.spec.whatwg.org/multipage/workers.html#dom-worker-postmessage) interface, and those pages can manipulate the DOM if needed.
* Is a programmable network proxy, allowing you to control how network requests from your page are handled.
* it's terminated when not in use, and restarted when it's next needed. There is an access to [IndexedDB API](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API) to handle state after restart.

### The life cycle

Life cycle is completely separate from the web page.

Should be registered first, this will cause the browser to start the SW install step in the background. It will cache some static assets during the installation phase. If assets cached SW then successfully installed. If any assets fail then the install step is failed =&gt; the SW is not activated, it'll try again next time.

When installed, the activation step will follow and this is a great opportunity for handling any management of old caches, which we'll cover during the service worker update section.

Once a service worker is in control, it will be in one of two states: either the service worker will be terminated to save memory, or it will handle fetch and message events that occur when a network request or message is made from your page.

![](../../.gitbook/assets/image%20%288%29.png)

### Registration

A service worker is first registered using the [`ServiceWorkerContainer.register()`](https://developer.mozilla.org/en-US/docs/Web/API/ServiceWorkerContainer/register) method. If successful, your service worker will be downloaded to the client and attempt installation/activation.

### Download, install, activate

The service worker is immediately downloaded when a user first accesses a service worker–controlled site/page.

**After that, it is updated when:**

* A navigation to an in-scope page occurs.
* An event is fired on the service worker and it hasn't been downloaded in the last 24 hours.



sources: 

* [Google intro to service workers](https://developers.google.com/web/fundamentals/primers/service-workers)
* [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API)

Learn more: 

* [The basic of workers](https://www.html5rocks.com/en/tutorials/workers/basics/)

