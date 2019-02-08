# Enforcing usage of Yarn

In order to enforce usage of Yarn, declare the following `preinstall` hook in your scripts in `package.json`:

```
"preinstall": "node -e \"if(process.env.npm_execpath.indexOf('yarn') === -1) (console.error('Please use Yarn instead of NPM to install dependencies. See: https://yarnpkg.com/lang/en/docs/install/'), process.exit(1))\"",
```
