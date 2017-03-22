# Bash tricks

#### Swapping a fragment of a previous command
```
^fcuk^fuck^
```

#### Simple file renaming (with paths)
```
mv /path/to/{old_file.js,new.file_js}
```

#### Displaying content of lines added to a file (np. showing current logs)
```
tail -f
```

#### Shortcut to refer to the last argument of the last command
```
$_
```

Example - how to get to the newly created directory quickly:

```
mkdir test
cd $_
```
