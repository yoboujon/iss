# Cloud and Edge Computing

## Course outline

**Cloud computing** is a term that represents the will to decentralize data and computation power. In a never-ending race for more powerful hardware and faster compute, having dedicated hardware available anywhere could be a solution.

The *Cloud* is based on what we call a SOA *(Service Oriented Architecture)*. This model focuses on multiple concepts such as fast deployment, reusability and services. Furthermore here are a list of key elements defining SOA:
- Service encapsulation.
- Low coupling of services, Reducing dependencies.
- Service abstraction, concealing the service logic from the outside world.
- Service reuse, sharing logic between several services with the intention of promoting reuse (with SOAP or REST APIs).

In this course we are going to go into details for such an abstraction layer. What software we use, what are the pros and cons of such an architecture, why is it used today in the Web 2.0. Some sensors or actuators can be triggered from a gateway, it may use heterogenous protocols, this is what SOA can achieve: making connectivity seamless.

## Technical aspects
### Service Oriented Computing *(SOC)*

With *SOA*/*SOC*, the goal would be for an application to have multiple services that are not dependant on each other. In this turn of event, they can communicate with various protocols such as *REST* or *SOAP*. These services can be updated independently, and accessed by the user as standalone applications. The difference with traditional software is the focus on modular programming.

> We are not going into details about *SOAP* or *REST*, we are just going to assume that services exchange data between them.

![schema_services]()

*SOC*/*SOA* focuses on multiple aspects such as :
- Business Value
- Strategic Guide
- Flexibility
- Intrinsic Inter-Operability
- Evolutionary Refinement
- Shared services

There are multiple roles for each services, 3 in particular, these are: **Owner**, **Provider** and **Consumer**. Each of them are directly influencing the other: The owner makes the provider which goes into the hand of the consumer. A fully usable service can be created into multiple micro-services. The goal: integrates once, deploy anytime.

![schema_services]()

