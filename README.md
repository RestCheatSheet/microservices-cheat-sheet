See also: [API Design Cheat Sheet](https://github.com/RestCheatSheet/api-cheat-sheet#api-design-cheat-sheet),
[Platform Building Cheat Sheet](https://github.com/RestCheatSheet/platform-cheat-sheet#platform-building-cheat-sheet)

# Microservices Cheat Sheet
1. Do only one thing and do it well. The "one thing" is defined by a "Bounded Context" in Domain-Driven Design (DDD).
1. Own your own data. No shared data stores.
1. Embrace eventual consistency.
    * Don't read your writes.
    * Publish your own state-changes (minimally) to an event log.
1. Leverage event logging and/or streaming to replicate and denormalize data from other services.
    * The event log must be subscribable to *publish* events to subscribers.
    * The event log must be durable and must not lose messages for publishing and replay.
    * Examples: [Kafka](http://kafka.apache.org/), [Confluent.io](http://www.confluent.io), [Amazon Kinesis](https://aws.amazon.com/kinesis/).
1. When aggregating microservice calls, use asynchronous, non-blocking I/O. Perform as much as possible asynchronously.
1. Support a registry/discovery mechanism.
    * Examples: [Consul](https://www.consul.io/), [Eureka](https://github.com/Netflix/eureka)
1. Support Location Transparency.
    * Support statelessness--no sticky sessions.
1. Support the use of back-pressure (see, Reactive Streams specification) to avoid cascading failures.
    * Examples: [RxJava](https://github.com/ReactiveX/RxJava/wiki/Backpressure)
1. Support the Circuit Breaker pattern to manage faulty service dependencies.
    * Examples: [Hystrix](https://github.com/Netflix/Hystrix), [Apache Zest](https://zest.apache.org/java/2.1/library-circuitbreaker.html)
1. Consider CQRS to scale reads separately from writes.
