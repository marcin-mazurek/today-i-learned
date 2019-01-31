# Code review checklist

### Code quality
- [ ] Code is clear and readable, there's no magic
- [ ] Code follows business nomenclature
- [ ] Unit and integration tests are written
- [ ] No unnecessary or outdated dependencies introduced
- [ ] Constants used for magical strings
- [ ] Only necessary comments added, workarounds described, discovered bugs and TODOs linked to a ticket
- [ ] Scout rule followed
- [ ] No memory leaks introduced - event listeners, open connections are cleaned up when not needed
- [ ] Edge cases taken into consideration
- [ ] Necessary logging added
- [ ] No unnecessary debugging code added
- [ ] Clear exceptions thrown, following fail fast principle

### Web development specific
- [ ] Semantic markup used
- [ ] `package-lock.json` / `yarn.lock` committed (if there are any changes to `package.json`)

### Cross-functional requirements
- [ ] Internationalisation supported (language, currency, date and time formatting)
- [ ] Analytics added (if applicable)
- [ ] HTTPS supported
- [ ] Network requests are retried in case of failure and fail gracefully (component hidden / last good known response served)

### Security and performance
- [ ] User input validated, whitelisted and/or escaped
- [ ] No injection vulnerability introduced
- [ ] No broken authentication or broken access control vulnerability introduced
- [ ] No XSS vulnerability introduced
- [ ] Bundle size verified and not made significantly worse
- [ ] Number and size of other assets loaded verified and not made significantly worse
- [ ] Cache and asynchronous loading introduced where possible
