# TypeScript versus Flow
* TS is a language, Flow is an additional syntax for JS which is stripped out during transpilation.
* TS has its own compiler, Flow can use any - additional syntax can be stripped out by a CLI tool or Babel plugin.
* TS used not to support non-nullable types, [now they can be turned on in compiler settings](https://github.com/Microsoft/TypeScript/pull/7140). Flow supports non-nullable types by default.
