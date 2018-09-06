# Techniques to build reliable distributed systems

## Circuit breaker

A technique used to prevent an unavailable service from overloading with requests. Circuit breaker monitors requests and when given number of subsequent requests fails, it prevents further requests from happening until the system recovers. Recovery can be detected by periodic checking of the healthcheck endpoint.

## Thundering herd protection

When the cached value is not available, before a new value is computed and stored, there can be multiple requests to obtain the same resource that will cause unexpected load.
To prevent that from happening, requests can be throttled, or new values can be recomputed before the cache expires.
