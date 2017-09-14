## Filter/filter out a file type
```
ack ... --js
ack ... --nojs
```
etc.

## Output formatting
Return only the regex capture groups:

```
ack 'process\.env\.([A-Z_]{3,})' -h --output='$1'
```

Will return e.g.:

```
BABEL_ENV
NODE_ENV
PORT
```

`-h` flag hides file names

## List only file names
```
ack ... --files-with-matches
```
