## Passing arguments to a script invoked by npm

If you want to pass parameters to e.g. `webpack` command which is invoked by `build` script, you need to use the following syntax:
```
npm run [command] -- [arguments]
```

Eg.
```
npm run build -- --watch
```
