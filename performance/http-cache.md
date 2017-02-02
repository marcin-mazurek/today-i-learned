# HTTP cache
## Cache-Control header
- `no-cache` - disallows getting a resource from cache without checking ETag with server
- `no-store` - disallows storing a file in cache (eg. for resources containing sensitive data)
- `public` - means that a resource is not dedicated for a particular user and may be cached by eg. a proxy server
- `private` - means that a resource cannot be shared with different users

The simplest approach to caching resources, if you have a full control over a URL: very long cache age + query string checksum.
This allows to avoid making requests to verify ETag and gives on-demand cache invalidation.
