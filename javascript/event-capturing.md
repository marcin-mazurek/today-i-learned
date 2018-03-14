# Event capturing
Event capturing is a less known phase of event processing in the DOM.

Each event actually starts from the top of the DOM hierarchy, which is `window`,
then it goes down once it reaches the actual element the event was triggered on (eg. a button).
After that, it bubbles up to the top (`window`) again.

Normally, when we add an event listener on a parent elements (eg. a div with a button inside), we rely on event bubbling:

```
const button = document.querySelector('button');

button.parentNode.addEventListener('click', () => console.log('Executed second'));
button.addEventListener('click', () => console.log('Executed first'));
```

However, `addEventListener` accepts a third parameter - a boolean telling whether to use event capturing (`true`) or bubbling (`false`, default value).

```
const button = document.querySelector('button');

button.parentNode.addEventListener('click', () => console.log('Executed first'), true);
button.addEventListener('click', () => console.log('Executed second'), true);
```

In practise - this means that the order of event handlers will be reversed, and prioritised over event bubbling handlers.

We can use this behaviour to prevent events reach the target element. 

```
const button = document.querySelector('button');

button.parentNode.addEventListener('click', evt => evt.stopPropagation(), true);
button.addEventListener('click', () => console.log('Not executed'), true);
```

A sample CodePen to try this out in practice: https://codepen.io/marcin-mazurek/pen/mxPRjM/?editors=1111
