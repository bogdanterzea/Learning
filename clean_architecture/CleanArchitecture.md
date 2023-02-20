# Clean Architecture 

## Layered Architecture

- it is the most common
- the predominant part of the applications got 3 layers and there may be up to 5 layers
- The most used format is : data, domain and presentation layers
- the layers doesn’t need to know more than 1 layer distance above or below them
- in order to reach to a specific layer, the information/action must pass between all the previous layers first
- layers of isolation concept - a change done in one layer doesn’t affect components in other layers
- suppose the majority of the data is passing through a layer without getting changes and just to be passed forward. In that case, you may consider passing the data through an open layer and letting that be accessed directly by the next layer.
- easy to test, develop and use but hard to change, maintain, and hard to migrate because all the layers may be affected.
---

## Event-Driven Architecture

- is split in two topologies, mediator and broker
    - mediator - a central mediator controlling multiple events around him
    - broker - events handled in chain without needing any mediator
- Mediator topology
    - it is constructed on 4 main components:
        - event queues
        - event mediator
        - event channels
        - event processors
    - Event queue → Event Mediator → Event Channels → Event processor
    - Benefits: decoupling, modularity(easy to remove components), control(easy to manage interactions)
- Broker topology
    - the events will be processed in chains one after another
    - This only needs 2 components:
        - broker
        - event processor
    - Benefits: decoupling, modularity, scalability
- to take in consideration when implementing it:
    - remote process availability
    - responsiveness
    - mediator possible failures
- This pattern may be hard to implement and test but it is scalable, performant, and easy to develop once it is implemented
---

## Microkernel Architecture

- It has two types of architectural components:
    - core system
    - plug-in modules
- The core system provides only the basic functionalities for the system to be operational.
- The plug-in modules are stand-alone components that are specialized on solving a specific problem/feature.
- The plug-is should stay independent one of another.
- The communication between plug-ins and the core should be minimal in order to avoid dependency issues.
- When the plug-ins are 3rd party with no control over them, it’s recommended to create adapters so that you won’t need more specialized code for that plug-in.
- This pattern is usually used in combination with other architectural patterns.
- This pattern offers the capability for quick changing of the environment; the Capability of quick development because plug-ins can be easily added; The capability to test independent functionalities;
- The pattern is not usually used for a highly scalable application.
---

## Microservices Architecture Pattern

- There are several core concepts of this pattern:
    - Separately deployed units - provides scalability
    - service component notion - this can contain from small functionalities to the entire business logic of the app
    - all the components are decoupled - distributed architecture
- this architecture splits the application in multiple deployable units that can be individually developed, tested and deployed.
- Pattern topologies:
    - API-REST based topology
        - useful for websites
        - this topology is useful for apps with small services. Each service is independent. Each service is accessed using a REST interface.
    - REST based topology
        - the request from the client will go directly to app business instead of a simple API interface
        - this app services will be larger
        - this topology is used for medium size applications
    - The centralized messaging topology
        - the advantages are asynchronous messaging, monitoring, error handling, and better scalability.
        - The difference is that after the user interface layer, the data will be handled by a lightweight message broker that will alter that data in the wanted way.
- The important part is to avoid dependencies and keep the services separated and clean.
- If a service component needs to do the same thing as another service component there will be duplicated code.
---

## Space-based Architecture

- The problem that this architecture fix is the scaling of an application to get more users. When an application scales, the database server will eventually get overwhelmed.
- The concept doesn’t implement a central database that shares the data inside the app and the data will be loaded with each component and destroyed father the specific thread of actions is done.
- This architecture is implemented on websites generally
- The components of the architecture are:
    - Processing unit - being modules for different purposes of the application and containing the base data and logic
    - Virtualized middleware - It contains objects responsible for data handling and synchronization.
- Pattern dynamics
    - In the virtualized middleware there are usually 4 components - messaging grid, data grid, processing grid and deployment manager
        - Messaging grid - this manages the input request and determines which component to receive the request
        - Data grid - This is the most important component. It ensures that each processing unit gets the same data. It syncs it very quickly.
        - Processing grid - Optional component that mediates the request between 2 processing units
        - Deployment manager - Opens and closes processing units because it monitors them.
- Conclusions:
    - Good overall(recommended for small websites)
    - Hard to implement
    - Hard to test
    - Good scalability!