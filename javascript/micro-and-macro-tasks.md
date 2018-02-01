# Microtasks and tasks in JavaScript

There's two types of event loop tasks: microtasks and tasks, also called macrotasks.

**Microtasks** can be scheduled during a macrotask execution, and those will be exectued before next **macrotask** will start.

To visualise, let's take a look at the diagram:

```
+----------------------------------+
|                                  |
|             EVENT LOOP           |
|                                  |
| +------------------------------+ |
| |                              | |
| |              Task            | |
| |                              | |
| | +--------------------------+ | |
| | |                          | | |
| | |         Microtask        | | |
| | |                          | | |
| | +--------------------------+ | |
| |                              | |
| | +--------------------------+ | |
| | |                          | | |
| | |         Microtask        | | |
| | |                          | | |
| | +--------------------------+ | |
| +------------------------------+ |
|                                  |
| +------------------------------+ |
| |                              | |
| |             Task             | |
| |                              | |
| +------------------------------+ |
|                                  |
|                ...               |
|                                  |
+----------------------------------+
```

An example for Node.js environment:

```javascript
const process = require('process');

setImmediate(() => console.log('macro task 5'));
setImmediate(() => console.log('macro task 6'));

setTimeout(() => console.log('macro task 2'), 0);

fs.readdir(process.cwd(), () => console.log('macro task 4')); // slower than setTimeout with 0ms delay

console.log('macro task 1'); // this is actually just a synchronous call, not a macro task - just to visualise in console output
process.nextTick(() => console.log('macro task 1: micro task 1'));
process.nextTick(() => console.log('macro task 1: micro task 2'));
process.nextTick(() => console.log('macro task 1: micro task 3'));

setTimeout(() => {
  console.log('macro task 3');
  process.nextTick(() => console.log('macro task 3: micro task 1'));
  process.nextTick(() => console.log('macro task 3: micro task 2'));
  process.nextTick(() => console.log('macro task 3: micro task 3'));
}, 0);
```

`process.nextTick` and `Promise.resolve()` schedule a microtask.
Any other asynchronous actions (eg. file system access), and timer intialisations (such as `setTimeout`), schedule a task.
To make things more difficult, any callback scheduled with `setImmediate` gets executed after everything else (including I/O operations).

For more details, check out Jake Archibald's blog post: https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/
