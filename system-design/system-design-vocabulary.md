# System design vocabulary

- **Idempotency** - if the operations are idempotent, the outcome doesn't change even if the operation is executed multiple times
- **Sticky sessions** is a method used with load balancing, to ensure that a user is always redirected to the same server, for a defined period of time.
- **Vertical scaling** - increasing capacity of hardware by adding resources eg. CPU or RAM
- **Horizontal scaling** - adding more machines to the resource pool
- **CAP theorem** - theorem in distributed systems that states any distributed system can have at most two of: consistency, availability and partition tolerance.
- **Backends for frontends** - a service exposed to the UI, handles data preparation and composing data into shape required by the front-end layer
