## How to kill a process running on a given port?

```
kill -9 $(lsof -t -i:8088)
```