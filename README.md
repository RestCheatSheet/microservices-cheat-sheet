See also: [API Design Cheat Sheet](https://github.com/RestCheatSheet/api-cheat-sheet#api-design-cheat-sheet),
[Platform Building Cheat Sheet](https://github.com/RestCheatSheet/platform-cheat-sheet#platform-building-cheat-sheet)

# Microservices Cheat Sheet
1. Do only one thing and do it well. The "one thing" is defined by a "Bounded Context."
1. Own your data.
1. Embrace eventual consistency.
1. Leverage eventing logging and/or streaming to replicate and denormalize data from other services.
    * Each microservice must (at least) publish its state-changes to the event log.
    * The event log must be subscribable to *publish* events to subscribers.
    * The event log must be durable and must not lose messages for publishing and replay.
1. When aggregating microservices, use asynchronous, non-blocking I/O and perform as much as possible asynchronously.
1. Support a registry/discovery mechanism.
1. Support Location Transparency.
1. Support statelessness--no sticky sessions.
1. Support the use of back-pressure (see, Reactive Streams specification) to avoid cascading failures.
1. Support the Circuit Breaker pattern to manage faulty service dependencies.
1. Consider CQRS to scale reads separately from writes.
