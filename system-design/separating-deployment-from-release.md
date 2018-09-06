# Separating deployment from release

- Blue/green deployment - technique of releasing a software to one of two identical production environments, and switching the routing from the old version to the new one after the release, allowing for zero-downtime deployment and immediate rollback
- Canary releases/dark launches - slowly rolling out changes to a subset of users, before rolling it out fully
- Feature toggles/feature switches/feature flags - enable deployment of features into production without making them visible to the end user
