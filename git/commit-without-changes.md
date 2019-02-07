# How to create a commit without changes?

If, for whatever reason (eg. triggering a release based on commit messages), you need to create an empty commit in Git, you can do that by passing `--allow-empty` argument to `git commit`:

```
git commit -m "release_type:patch" --aloow-empty
```
