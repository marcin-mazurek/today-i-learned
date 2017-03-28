# JS tricks and less known features
## How many arguments does a function accept?
```
function myFn(a, b, c, d) {}
console.log(myFn.length); // 4
```

## How to compare objects with `>` and `<` operators?
```
class EmployeeID {
  constructor(id) {
    this.id = id;
  }
  valueOf() {
    return this.id; // eg. 149
  }
}

const firstEmployeeID = new EmployeeID('1');
const lastEmployeeID = new EmployeeID('150');

console.log(lastEmployeeID > firstEmployeeID); // true
console.log(firstEmployeeID > lastEmployeeID); // false
```
