# Changing settings from command line
`defaults` is a command line tool that allows to change application and system settings on macOS.

Settings are divided into domains (eg. system feature, app). You can list all domains with:
```
defaults domains
```

You can list one domain's settings with:
```
defaults read [domain]
```

Global settings are stored under `NSGlobalDomain`, you can also use `-g` shorthand to refer to it.

Finally, you can set a particular option with the following command:
```
defaults write [domain] [option] [value]
```
Where value is `-bool true` or `-bool false` for a boolean or just the value for a string.

For examples, please refer to my [settings](https://github.com/marcin-mazurek/settings/blob/master/mac-setup/set-up-mac.sh) repo.
