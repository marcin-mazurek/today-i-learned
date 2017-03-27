# Overriding the author for a single repository

```
git config --local user.email "marcin@mazurek.pro"
```

## Overriding the author of n last commits
git rebase -i HEAD~[n last commits] -x "git commit --amend --author 'Author Name <author.name@mail.com>' --no-edit"
