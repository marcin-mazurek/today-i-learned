# Devtools tricks
## Less known console APIs
### console.count(key)
Session-time debugging counter:

```
console.count('foo');
console.count('foo');
console.count('foo');
```
Outputs: 
```
foo: 1
foo: 2
foo: 3
```
