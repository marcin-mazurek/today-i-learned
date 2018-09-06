# Proxies

- Forward proxy - also known just as "proxy", is a proxy that handles traffic from a client to server. It can be used to anonymise the client, filter content, may be combined with a cache to lower bandwidth usage.
- Reverse proxy - accepts a request from a client, forwards it to a server that can fulfill it, and returns the server’s response to the client. Can be used to handle application delivery, manage traffic, load balancing, SSL decryption, compression, DoS protection, etc. Examples: [Nginx](https://www.nginx.com/)
- Caching proxy - a type of reverse proxy, that specializes in caching server responses. Examples: [Varnish](https://varnish-cache.org/), [Squid](http://www.squid-cache.org/)
