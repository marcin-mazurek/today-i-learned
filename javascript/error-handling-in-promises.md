# Error handling in Promises

Promise errors can be handled in two ways:

Two parameters passed to the `then` call:

```
promise.then(
  () => { /* resolve */ }, 
  () => { /* reject */ }
);
```

And with separate `catch` call:

```
promise.then(
  () => { /* resolve */ }
).catch(
  () => { /* reject */ }
);
```

The latter allows to catch errors in Promise chains (one Promise returning another) and **allows to catch errors in** `then` **callback itself**.
