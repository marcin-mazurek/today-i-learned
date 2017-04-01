# Bash tricks

#### Swapping a fragment of a previous command
```sh
^fcuk^fuck^
```

#### Simple file renaming (with paths)
```sh
mv /path/to/{old_file.js,new.file_js}
```

#### Displaying content of lines added to a file (np. showing current logs)
```sh
tail -f
```

#### Shortcut to refer to the last argument of the last command
```sh
$_
```

Example - how to get to the newly created directory quickly:

```sh
mkdir test
cd $_
```
