# Different ways of loading a JS scripts
- standard `<script />` tag - pauses execution until a script has been loaded
- `<script defer />` - browser continues with parsing HTML content, sripts are executed after HTML is parsed (but before `DOMContentLoaded` event) in declaration order. **Caveat**: the order is not guaranteed in IE9 due to a [bug](https://github.com/h5bp/lazyweb-requests/issues/42)
- `<script async />` - downloaded during HTML parsing, will pause the HTML parser to execute the script when it's been downloaded. Async scripts shouldn't modify the DOM.

A more detailed explanation here: http://www.growingwiththeweb.com/2014/02/async-vs-defer-attributes.html
