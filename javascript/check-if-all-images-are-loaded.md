## How to programatically check if all images on a page are loaded?

```
Array.from(document.images).some(img => img.complete !== true)
```
