# Introduction

## From Monoliths to Microservices

authonomy
> Distributed systems are here to stay. If you don‘t like it, change careers. Maybe open a restaurant. - Vaughn Vernon

# Fundamentals

## Coupling

In the Enterprise Integration Patterns book, Gregor Hohpe and Booby Woolf defined the notion of coupling by the number assumptions two systems make about each other when they communicate.

## Communication

## Distributed computing

https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing

## Synchronous vs Asynchronous

## Concurrency vs Parallelism

## Autonomy vs Authority

> The ability to make your own decisions without being controlled by anyone else - Cambridge Dictionary
> Authority is the right to command and control other people - Cambridge Dictionary

//Notes from Reduce Reuse Recycle
Don't Repeat Yourself (DRY) principle
The more widely shared, the more flexible it must be
The price of stability is overhead and governance – administrative complexity
Infrastructure overhead & single point of failure which may come from poorly planned reuse
>  Complexity trumps reuse. Reuse is not our goal, it is a possible path to our goal. And more often than not, it isn’t even a path, it is a distraction. Our real goal is not more reusable IT systems, it is simpler IT systems. Simpler systems are cheaper to build, easier to maintain, more secure, and more reliable. That is something you can bank on. Unlike reuse.

Rather than naively assuming that code reuse always lowers costs, it must be evaluated taking the costs and risks noted above into account. Reuse should only be pursued where the actual costs are outweighed by the benefits.


## Integrity vs Consistency

## References

[1] [Enterprise Integration Patterns](https://www.amazon.com/dp/B007MQLL4E)

[2] [Reduce, Reuse, Recycle](https://www.amazon.com/dp/B007MQLL4E) by Gene Hughson

# Service Orientation

In 2009, Anne Thomas Manes a Gartner analyst published an famous post relate to SOA.

> SOA is Dead; Long Live Services - Anne Thomas Manes

Basically, she explained that, in most cases, service-oriented architectures failed to deliver the expected benefits.

> After investing millions, IT systems are no better than before. In many organizations, things are worse: costs are higher, projects take longer, and systems are more fragile than ever. - Anne Thomas Manes

The main reason for this failure, according to her, is that IT people did not take enough time to think about the main concept of SOA: the notion of service.

> People forgot what SOA stands for. They were too wrapped up in silly technology debates (e.g., “what’s the best ESB?” or “WS-* vs. REST”), and they missed the important stuff: architecture and services.

Yet, she believed the service-orientation remained a must-have for IT systems.

> Although the word “SOA” is dead, the requirement for service-oriented architecture is stronger than ever.

This post was simply delightful and ahead of its time. Today, the industry is convinced service-orientation is a must-have. Regardless if we speak about web services, REST services or microservices, the base concept remains the same: the service.

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

//TODO diagram

The last principle is for me the most interesting to discuss about:

8. Service autonomy

At first sight, this principle is a contradiction of service composability. The more a service is a sequence of other service calls, the less autonomous it is. Yet, this is not absolutely true.

In case of a synchronous orchestration for example, this statement is completely valid. The service orchestrating the composed services has a temporal dependencies with every services.
On the other hand, if we take the case of an asynchronous choreography, the orchestrating service does not depend anymore on the availability of the composed services.

Furthermore, inter-service dependencies is not the only way for a service to loose autonomy. What if our services needs to share some data and that we chose to make them all dependent on the same database? In such cases, our services will obviously loose autonomy.

In my opinion, this is the biggest mistake of SOA architects. In many SOA implementations, we can found such services which are temporally dependent with serveral other services. This led to an overall system fragility.

//TODO diagram

What if service X is unavailable? It simply impacts the whole system. //Etc...

Before the service paradigm, the base asset was the application. In many systems, the applications were autonomous. //TODO to be continued

For me, microservices architecture are absolutely not different from the initial SOA philosophy. Yet it empasizes two things:
* Service granularity to improve service reuse and composability
* Service autonomy to decrease cascading failures

## API Management

## Microservices Architecture

## Middlewares

## Containers

## References

[1] http://apsblog.burtongroup.com/2009/01/soa-is-dead-long-live-services.html
[2] http://soapatterns.org/files/SOA_Principles_Poster.pdf

# Event-Based Systems

## Messaging Broker

Message ordering
Envelope

> There are only two hard problems in distributed systems: 2. Exactly-once delivery 1. Guaranteed order of messages 2. Exactly-once delivery - Mathias Verraes

## Streaming architectures

# Reactive Architectures

https://fr.slideshare.net/jboner/from-microliths-to-microsystems

## Reactive Programming

## Reactive Systems

## The Actor Model

# Data Governance

## Domain Driven Design

## Canonical Data Model

A canonical data model (CDM) is defined in the Enterprise Integration Patterns book as a solution to minimize dependencies when integrating applications using different data formats. Thus, a CDM must be independent from any specific application.
It is worth mentioning this concept should be used only as a transport data format. We would not want to use a CDM as an internal data model of a database for example.

Theoretically, the advantages of a CDM are pretty obvious. It would help reducing the coupling between the applications, reducing the number of translations to be implemented for integrating a set of components etc. Pretty sexy right? One single data model, understandable by the whole landscape and a rich set of people (developers, system analysts, business stakeholders etc.) who could share the very same vision of a given concept.

Nonetheless, in large organizations, it is very unlikely that such models will really deliver its expected added value.
The reason is quite simple. Large organizations are complex by nature. A person is not the same concept for a marketing and a support department in an insurance company. A PLM part has a complete different representation depending if has been drafted by a designer of if it has to be maintained by a support team. //TODO Another example

Most of the implementations result in having a very large model with a large set of optional attributes and very few mandatory ones (like an identifier but depending on the domain complexity, this is not even sure). Even though the main goal of a CDM was to ease components integration, we will just complicate it. Meanwhile, such models are creating for regular users a lot of frustrations because of its inherent complexity in terms of utilization, management, evolution impacts etc.

Furthermore, regarding the coupling challenge, we just shift it somewhere else. Instead of being coupled to an external component data format, we become coupled to a common data format that would be used by the whold IT landscape and suject to very frequent changes.

In my opinion, in most contexts a CDM should not be an appropriate answer. Yet, what whould the the other option if we still want to minimize the dependencies between two components when exchanging data?

DDD introduces the concept of bounded context. A bounded context is simply an explicit context in which a model applies with clear boundaries with other bounded contexts. Depending on your organization a bounded context could refer to
 * A functional domain in which an object is utilized
 * An object state
 * Etc.

In that case the canonical data model as such would simply be the yelow part in the following diagram:

//TODO diagram

The intersection of A, B and C represents the set of attributes that must be there regardless of the context (basically the mandatory attributes of the previous large CDM). This part should still be carefully designed due to its central role. Yet it is important to remain pragmatic. If in your context is does not make sense to have such common model, you should simply discard it.

What is also important is an intersection between two contexts (A and B, B and C, C and A). How to map one object representation from one context to another? What are the explicit attributes that should be shared across two contexts? What are the common business constraints between two contexts? These questions should still be answered by a transverse team but from a business perspective, it makes sense to raise them. That was not always the case with one single CDM shared across potentially opposite contexts.

Nonetheless, regarding the parts which are not shared with other contexts (in white), it should not be part of an enterprise data model. You should be pragmatic. For example, if a subset is specific to a given domain, it should be up to the domain experts to model it themselves.

One key challenge, though, is to identify those bounded contexts and it might be worth reminding here the Conway’s law:

> Any organization that designs a system will inevitably produce a design whose structure is a copy of the organization’s communication structure - Melvin Conway

The bounded contexts shall not be necessarily mapped onto the current organization. For example, a bounded context can encompass several departments. Bear in mind if you company is siloed, trying to break them should still be an objective. Yet, we must remain pragmative. It is very unlikely that we will achieve a single vision and a single representation for a master data.

//TODO find a transition

In addition DDD introduces the concept of Anti-Corruption Layer (ACL). This pattern can refer to a solution for a legacy migration (by introducing an intermediation layer between the old and the new system to prevent data quality issues etc.). But in our context when we talk about corruption it is related to data modeling debt you can introduce to solve short-term problems.

Let us take the example of two systems in charge to manage a given state of a PLM part (a part is a physical item produced or purchased and then assembled like a helicopter rotor for instance). One legacy system (let’s call it SystemA) is in charge to manage the design phase and you must implement a new system (let’s call it SystemZ) in charge to manage the maintenance phase. The whole IT application landscape shares the same common part identifier (partId) except for SystemA which is not aware of it. Instead of the partId, SystemA manages its own identifier, systemAId. Because SystemZ needs to be call SystemA using systemAId, a heuristic could be to integrate systemAId as part of the SystemZ data model.

This is a common mistake you should avoid. You simply corrupted your data model because of a short-term situation.

The ACL pattern could have been a solution here. SystemZ could have implemented its own data format (without any external corruption like the systemAId). Then it would have been up to an intermediation layer to manage the translation between the partId and the systemAId.

Applied to our topic, the ACL pattern enforces to implement a layer in between two different bounded contexts. A component is not aware of how to call another component which is not part of its own bounded context. Instead, a component is only aware of how to map its own data structure on the data format of the bounded context it belongs to.

By the way, this is a rule of thumb. A component shall belongs to only one bounded context. This is also why DDD is a great fit for microservices architecture. Because of the fine-grained granularity, it is easier to comply with this rule.

## References

[1] [Enterprise Integration Patterns](https://www.amazon.com/dp/B007MQLL4E)

[2] [Domain-Driven Design](https://www.amazon.com/dp/B00794TAUG/)

## Master Data Management

//TODO MDM article

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

# What's next?
