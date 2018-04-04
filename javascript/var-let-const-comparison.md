## Adding a property to a global object
When declared in global context, `var` adds a property to a global object:
```
var test = 'foo';
console.log(window.test); // 'foo'
```
  
`let` and `const` never adds a property to global object:
```
let test2 = 'foo';
const test3 = 'bar';
console.log(window.test2); // undefined
console.log(window.test3); // undefined
```
