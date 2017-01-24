# Resizing an iframe on content changes
If you need to listen to DOM changes in an iframe and resize it when something changes, you can use the [MutationObserver API](https://developer.mozilla.org/en/docs/Web/API/MutationObserver).

Here's an example how to adjust the iframe height when a change in DOM occurs:

```js
const iframe = document.querySelector('iframe');
const iframeDocument = iframe.contentWindow.document;
const observer = new MutationObserver(() => {
  iframe.height = iframeDocument.clientHeight;
});

observer.observe(iframeDocument, {
  subtree: true, attributes: true, childList: true, characterData: true,
});
```
