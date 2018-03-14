# Feature detection in CSS
## Feature query
Feature queries allow to specify declarations that depend on a browser's support for a particular feature. It has the following syntax:

```
@supports (display: grid) {
  /* when the grid layout is available */
}
```

It accepts negations:

```
@supports not (display: grid) {
  /* when the grid layout is unavailable */
}
```

It can also work with multiple properties:

```
@supports ((display: flex) or (display: -webkit-flex)) {
   /* ........ */
}
```

Browser support: https://caniuse.com/#feat=css-featurequeries (mostly everything but IE11)
