# Unblocking the event loop

The code snippet below demonstates a few different ways to unblock the event loop and their priority:

```js
const fs = require('fs');
fs.readdir(process.cwd(), () => {
  console.log('Fourth operation - fetching the current directory is an I/O operation that takes '
    + 'a bit of time. Therefore, despite being declared at the very top, the thread becomes free '
    + 'until we get the result from the file system and executes the callback from setTimeout(fn, 0).');
});

setImmediate(() => console.log('Fifth operation - a callback passed to setImmediate(fn) '
  + 'will be executed once all I/O actions are completed.'));

process.nextTick(() => {
  console.log('Second operation - process.nextTick(fn) sends an operation to the top of '
    + 'the event queue (well, can we really call it a queue then?!). '
    + 'The callback is executed as soon as all calls from the frame stack are finished.');
});

setTimeout(() => console.log("Third operation - setTimeout(fn, 0) is executed once the action " + 
  "from process.nextTick(fn) is completed."), 0);

console.log("First operation - just a synchronous call, doesn't go to the event loop. "
  + "If you perform a long running operation, it's recommended not to do it synchronously " +
  'to avoid blocking the event loop for a long time.');
```

The above snippet will output the following:

```
First operation - just a synchronous call, doesn't go to the event loop. If you perform a long running
operation, it's recommended not to do it synchronously to avoid blocking the event loop for a long time.

Second operation - process.nextTick(fn) sends an operation to the top of the event queue (well, can we
really call it a queue then?!). The callback is executed as soon as all calls from the frame stack
are finished.

Third operation - setTimeout(fn, 0) is executed once the action from process.nextTick(fn) is completed.

Fourth operation - fetching the current directory is an I/O operation that takes some time. Therefore,
despite being declared at the very top, the thread becomes free until we get the result from the file
system and executes the callback from setTimeout(fn, 0).

Fifth operation - a callback passed to setImmediate(fn) will be executed once all I/O actions are
completed.
```

Read more about the Node.js event loop: https://nodejs.org/en/docs/guides/event-loop-timers-and-nexttick/
