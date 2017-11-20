# Introduction

## From Monoliths to Microservices

authonomy
> Distributed systems are here to stay. If you don‘t like it, change careers. Maybe open a restaurant. - Vaughn Vernon

# Fundamentals

## Coupling

## Communication

https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing

### Synchronous vs Asynchronous

## Concurrency vs Parallelism

## Autonomy vs Authority

> “The ability to make your own decisions without being controlled by anyone else” - Cambridge Dictionary
> “Authority is the right to command and control other people.” - Cambridge Dictionary

# API management

# Microservices architecture

In 2009, Anne Thomas Manes a Gartner analyst published an famous post relate to SOA.

> SOA is Dead; Long Live Services - Anne Thomas Manes

Basically, she explained that, in most cases, service-oriented architectures failed to deliver the expected benefits.

> After investing millions, IT systems are no better than before. In many organizations, things are worse: costs are higher, projects take longer, and systems are more fragile than ever. - Anne Thomas Manes

The main reason for this failure, according to her, is that IT people did not take enough time to think about the main concept of SOA: the notion of service.

> People forgot what SOA stands for. They were too wrapped up in silly technology debates (e.g., “what’s the best ESB?” or “WS-* vs. REST”), and they missed the important stuff: architecture and services.

Yet, she believed the service-orientation remained a must-have for IT systems.

> Although the word “SOA” is dead, the requirement for service-oriented architecture is stronger than ever.

This post was simply delightful and ahead of its time. Today, the industry is convinced service-orientation is a must-have. Regardless if we speak about web services, REST services or microservices, the essential concept remains the same: the service.

Yet, if we take a look in the past, we cannot really say SOA was originally far from microservices architecture.

Let us now check at the eight fundamentals principles of the service concept defined by Thomas Erl. We will start by summarizing the first six principles and we will detail the last two ones.

1. Standardized service contract: A contract describing the functional and technical behavior of a service.
2. Service loose coupling: This characteristic is a direct benefit from the first principle. Because the service consumer is not direcly tight to the service implementation, it favors loose coupling.
3. Service abstraction: Again a direct benefit of the service contract. A service provides an abstraction in terms of technology, implementation etc. A sort of black box for a service consumer.
4. Service reusability: Probably the most expected principle of SOA. Without reuse, services-based architectures are a complete failure.
5. Service statelessness: A service should be as much as possible stateless for obvious scalability reasons.
6. Service discoverability: A service shall be discoverable in a service repository.

Except maybe for the latter which is, in my opinion, a complete failure because of standard failures (UDDI was too complex etc.), the other principles are still valid for any services-based architecture.

Let us now take a look at the seventh:

7. Service composability

The logic is straightforward. To be composable, a service designer must take care about its granularity. A coarse-grained service is hardly composable. On the opposite, a fine-grained service is easily composable and can be efficiently part of a broader system. 

//TODO: diagram

The last principle is for me the most interesting to discuss about:

8. Service autonomy

At first sight, this principle is a contradiction of service composability. The more a service is a sequence of other service calls, the less autonomous it is. Yet, this is not absolutely true.

In case of a synchronous orchestration for example, this statement is completely valid. The service orchestrating the composed services is tighly coupled with every service in terms of availability.
On the other hand, if we take the case of an asynchronous choreography, the orchestrating service does not depend anymore on the availability of the composed services.

Furthermore, inter-service dependencies is not the only way for a service to loose autonomy. What if our services needs to share some data and that we chose to make them all dependent on the same database? In such cases, our services will obviously loose autonomy.

In my opinion, this principle was by far the less understood by SOA architects. In many SOA implementations we can services which are everything but autonomous.

//TODO: diagram

What if service X is unavailable? It simply impacts the whole system. //Etc...

For me, microservices architecture are absolutely not different from the initial SOA philosophy. Yet it empasizes two things:
* Service granularity to improve service reuse and composability
* Service autonomy to decrease cascading failures

## References

[1] http://apsblog.burtongroup.com/2009/01/soa-is-dead-long-live-services.html

[2] http://soapatterns.org/files/SOA_Principles_Poster.pdf

# Data Governance

## Domain Driven Design

## Canonical Data Model

# Data Persistence

## ACID vs Base

http://www.allthingsdistributed.com/2008/12/eventually_consistent.html

## CAP Theorem

### Cloud Spanner

## CQRS

## Event Sourcing

# Performance

Load distribution

> People who are more than casually interested in computers should have at least some idea of what the underlying hardware is like. Otherwise the programs they write will be pretty weird. - Daniel Knuth

# Scalability

3 dimensions

# Resiliency

# Security

# Logging & Monitoring

# Event-Based Systems

## Messaging Broker

Message ordering
Envelope

# The Role of Middleware in Distributed Systems

# Reactive Architectures

https://fr.slideshare.net/jboner/from-microliths-to-microsystems

## Reactive Programming

## Reactive Systems

### The Actor Model

# What's Next?
