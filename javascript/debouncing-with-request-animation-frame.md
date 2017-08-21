# Debuncing with `requestAnimationFrame`
You can simply accomplish smooth debouncing without arbitrary values with `requestAnimationFrame`:

```js

function debounceWithRAF(callback) {
  let frameRequested = false;
  
  return () => {
    if (frameRequested) return;    
    frameRequested = true;
    
    requestAnimationFrame(() => {
      callback();
      frameRequested = false;
    });
  });
}

window.addEventListener('scroll', debounceWithRAF(fn));

```
