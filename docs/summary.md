---
author: [Felicitas Pojtinger]
date: "2022-12-17"
subject: "Uni Distributed Systems Summary"
keywords: [distributed-systems, hdm-stuttgart]
subtitle: "Summary for the distributed systems course at HdM Stuttgart"
lang: "en"
---

# Uni Distributed Systems Summary

## Meta

### Contributing

These study materials are heavily based on [professor Kriha's "Verteilte Systeme" lecture at HdM Stuttgart](https://www.hdm-stuttgart.de/vorlesung_detail?vorlid=5212233) and prior work of fellow students.

**Found an error or have a suggestion?** Please open an issue on GitHub ([github.com/pojntfx/uni-distributedsystems-notes](https://github.com/pojntfx/uni-distributedsystems-notes)):

![QR code to source repository](./static/qr.png){ width=150px }

If you like the study materials, a GitHub star is always appreciated :)

### License

![AGPL-3.0 license badge](https://www.gnu.org/graphics/agplv3-155x51.png){ width=128px }

Uni Distributed Systems Notes (c) 2022 Felicitas Pojtinger and contributors

SPDX-License-Identifier: AGPL-3.0
\newpage

### Course Timeline

This course on distributed systems covers a range of topics related to the design, implementation, and management of distributed systems. The course is divided into several sections, including:

1. **Introduction to distributed systems**: This section provides an overview of distributed systems and their key characteristics.
2. **Theoretical models of distributed systems**: This section covers the use of theoretical models, such as queuing theory and process and I/O models, to understand and analyze distributed systems.
3. **Message protocols**: This section covers the use of message protocols, including delivery guarantees, causality, and reliable broadcast, to facilitate communication between components in a distributed system.
4. **Remote procedure calls**: This section covers the use of remote procedure calls (RPCs) to invoke functions on a remote machine, as well as different RPC mechanisms such as marshaling, thrift, and gRPC.
5. **Remote objects and frameworks**: This section covers the use of remote objects and frameworks, such as RMI and EJB, to enable communication between objects in a distributed system.
6. **Theoretical foundations of distributed systems**: This section covers key concepts and theories that are relevant to the design of distributed systems, including the FLP theorem, time, causality, consensus, eventual consistency, and optimistic replication.
7. **Distributed services and algorithms I**: This section covers the design and implementation of various distributed services and algorithms, including load balancing, message queues, caching, and consistent hashing.
8. **Distributed services II**: This section covers more advanced topics in distributed services, including persistence, transactions, eventual consistency, and coordination.
9. **Distributed security**: This section covers the key considerations for securing distributed systems, including authentication, authorization, and access control (AAA), secure delegation, and backend security.
10. **Design of distributed systems**: This section covers the methodology and principles for designing distributed systems, as well as examples of different architectures and design patterns.
11. **System management in distributed systems**: This section covers the key considerations for managing and maintaining distributed systems, including monitoring, chaos monkeys, and patterns of resilience.
12. **Service architectures**: This section covers different service architectures, including service-oriented architecture (SOA) and microservices.
13. **Peer-to-peer systems and the distributed web**: This section covers the use of peer-to-peer systems and technologies, such as distributed hashtables, blockchain, onion routing, and distributed consensus, in the context of the distributed web.
14. **Ultra-large-scale systems**: This section covers the design and implementation of ultra-large-scale systems, including considerations related to scalability, performance, network design, and datacenter design.

## Introduction to Distributed Systems

### Overview

1. Definition of a distributed system (DS)
2. Challenges for developers working with DS
3. Reasons for using a DS
4. Examples of DS
5. Characteristics of DS
6. Middleware for DS
7. Concepts and architectures in DS, including scale, parallelism, and latency
8. Resources related to DS

### Definition of a Distributed System

A system that is made up of independent agents that interact with each other and produce a cohesive behavior. The interactions and events in this system happen concurrently and in parallel, meaning that they occur simultaneously and independently of one another. This type of system is often used to perform tasks that are too complex or large for a single agent to handle, and the concurrent and parallel nature of the interactions allows for efficient and effective processing of the tasks.

### Emergence

Four types of emergence: strong emergence, weak emergence, evolutionary emergence, and constructed emergence.

- **Strong emergence** refers to situations where it is not possible to predict what will emerge from the interactions of the system.
- **Weak emergence** refers to situations where simple principles combine to produce surprising results.
- **Evolutionary emergence** refers to the complex but robust development of a system over time, such as the transformation of an egg into a human being.
- **Constructed emergence** refers to the complex but often not robust emergence of a system that has been intentionally designed, such as a distributed system.

**Emergent failure modes**: Instances of cascading failures in constructed emergence.

### Why Distributed Systems hard for Devs?

- One reason is **emergence**, which refers to the complex and often unexpected behaviors that can arise when multiple components of a system interact with each other.
- Another reason is the **single machine view**, which can make it difficult to understand and debug issues that arise in a distributed system.
- **Errors** are also an inherent part of distributed systems, and developers must be prepared to handle and troubleshoot these errors.
- Additionally, there is no **"free lunch"\*** in distributed systems, meaning that there is always some trade-off or cost associated with every design decision.
- Finally, developing a distributed system involves **total end-to-end system engineering**, which can be a complex and time-consuming process.
- All distributed systems algorithms are also **based on the failures that are expected** and how they are handled, which can add to the complexity of developing a distributed system.

### Why Distribute a System?

There are several reasons why an organization might choose to use a distributed system:

- **Robustness/resilience**: Distributed systems are designed to be resistant to single points of failure, which makes them more resilient and able to handle unexpected issues. This can be achieved through techniques such as replication, which allows data to be stored on multiple servers to ensure that it is still available even if one server fails.
- **Performance**: Distributed systems can be designed to split processing into independent parts, which can improve overall performance by allowing different parts of the system to operate in parallel.
- **Scalability/throughput**: Distributed systems can be designed to handle large numbers of requests per second, making them well-suited for applications that need to scale to handle high levels of traffic.
- **Security**: Distributed systems can be used to create different security domains, which can help to protect sensitive data and ensure that it is only accessed by authorized users.
- **Price per request**: Distributed systems can be designed to use cheaper horizontal scaling or free resources, which can help to reduce the cost of processing each request.

### Examples of Distributed Systems

There are many examples of distributed systems, including:

- **Energy grids and telecom networks**: These systems distribute electricity and communication signals across large geographic areas, often using complex networks of wires and other infrastructure.
- **Villages, towns, and cities**: These systems are examples of distributed systems that are made up of many interconnected parts, including homes, businesses, roads, and other infrastructure.
- **IT infrastructure of large companies**: Many large companies rely on distributed systems to manage their IT infrastructure, including servers, storage, and networks.
- **High-performance clusters**: These systems are used to perform complex calculations and simulations, often in scientific or technical fields.
- **Google, Facebook, and other internet companies**: These companies rely on distributed systems to power their online platforms and services, including search, social networking, and advertising.
- **The web**: The internet itself is a distributed system, made up of millions of interconnected servers and devices that share information and resources.
- **The human body, organizations, and states**: These systems are examples of distributed systems that are made up of many interconnected parts, each of which plays a specific role in the overall functioning of the system.
- **A flock of birds**: A flock of birds is an example of a distributed system in nature, with each bird communicating and coordinating with the others to achieve a common goal.

### Characteristics of Distributed Systems

- **Influence of distribution topology and remoteness**: The physical layout of a distributed system and the distance between its components can have a significant impact on its performance and behavior.
- **Emergent behaviors and concurrent events**: Distributed systems can exhibit complex and often unexpected behaviors as a result of the interactions between their components. Concurrent events, in which multiple parts of the system are executing at the same time, can also contribute to this complexity.
- **Few analytic solutions and few model-based approaches**: There are often few analytic solutions or model-based approaches available for understanding and predicting the behavior of distributed systems, which can make them challenging to design and debug.
- **Heterogeneous components**: Distributed systems often consist of a wide variety of components, each with its own hardware, software, and other characteristics. This can make it difficult to ensure that all components are compatible and work together effectively.
- **No global time**: In a distributed system, there is no single, global clock that all components can use to coordinate their activities. This can make it difficult to synchronize the actions of different parts of the system.
- **A strong need for security**: Distributed systems often handle sensitive data or perform critical functions, which makes security a key concern.
- **Concurrency, parallelism, and replication**: Distributed systems often rely on concurrency, parallelism, and replication to improve performance and resilience.
- **Failure models define everything**: The design and behavior of distributed systems are often shaped by the failure models that are used to define how the system should respond to different types of failures.

### Eight Fallacies of Distributed Computing

- **The network is reliable**: This fallacy assumes that the network is always available and that communication between components will always be successful. In reality, networks can experience outages or other problems that can disrupt communication.
- **Latency is zero**: This fallacy assumes that there is no delay in communication between components, which is not always the case. Latency, or the time it takes for a message to travel from one component to another, can vary depending on the distance between components and other factors.
- **Bandwidth is infinite**: This fallacy assumes that there is an unlimited amount of capacity available for transmitting data, which is not always the case. Network bandwidth is a finite resource that can become congested, leading to slower communication speeds.
- **The network is secure**: This fallacy assumes that the network is invulnerable to security threats, such as hacking or data breaches. In reality, networks can be vulnerable to these types of threats, and it is important to implement appropriate security measures to protect against them.
- **Topology doesn't change**: This fallacy assumes that the physical layout of the network, or its topology, will not change over time. In reality, the topology of a network can change due to factors such as the addition or removal of components or changes in the physical infrastructure.
- **There is one administrator**: This fallacy assumes that there is a single person or group responsible for administering the network, which is not always the case. Distributed systems can have multiple administrators, each with different responsibilities and roles.
- **Transport cost is zero**: This fallacy assumes that there is no cost associated with transmitting data over the network, which is not always the case. In reality, there are often costs associated with networking, including hardware and software expenses and maintenance costs.
- **The network is homogeneous**: This fallacy assumes that all components of the network are the same, which is not always the case. In reality, distributed systems often consist of a variety of components with different hardware, software, and other characteristics.

### Programming Languages and Distributed Systems

There are two main approaches to programming languages and distributed systems: the transparency camp and the message camp.

The **transparency camp** focuses on hiding the complexity of a distributed system from the programmer. This can be achieved through techniques such as creating type-safe interfaces and calls, and hiding security, storage, and transactions behind frameworks such as .NET or Enterprise Java Beans (EJBs). This approach treats the distributed system as a programming model, rather than something that requires special handling.

The **message camp**, on the other hand, takes a more direct approach to programming distributed systems. This approach typically involves using a simple create, read, update, delete (CRUD) interface and using message content as the interface. Messages are often coarse-grained, meaning that they carry a large amount of data in a single message, often in the form of documents. Programmers in this camp deal with the complexity of remoteness directly, and architectures are often event-based or based on the representational state transfer (REST) model.

### History of Distributed Systems

The history of distributed systems can be divided into several distinct periods:

- **1950s-1980s**: During this period, basic research was conducted on topics such as time, consensus, and computability, which laid the foundations for the development of distributed systems.
- **1990s**: In the 1990s, distributed systems were used to connect Intranet applications using technologies such as Common Object Request Broker Architecture (CORBA), Remote Procedure Calls (RPC), and Distributed Component Object Model (DCOM). Client-server web servers also became popular during this period. Programming models dominated the design and development of distributed systems.
- **2000s**: In the 2000s, distributed systems were used to power peer-to-peer software for file sharing and large social sites emerged, which posed new challenges in terms of scalability and performance. Message passing and parallel batch processing techniques such as map/reduce were developed to address these challenges. This period also saw the emergence of in-memory computing and the CAP theorem, which established that it was not possible for a distributed system to simultaneously provide all three of the following properties: consistency, availability, and partition tolerance.
- **2010 and beyond**: In the 2010s and beyond, distributed systems have been used to power large-scale warehousing systems, fan-out architectures, and real-time stream processing. Flash memory and network performance have become key considerations, and microservices and serverless computing have emerged as popular approaches to designing and building distributed systems.

### Metcalfe's Law

Metcalfe's law is a principle that states that the value or utility of a network increases as the number of users in the network increases. This is because the more people who are using the network, the more useful it becomes as a platform for communication, collaboration, and the exchange of information and resources. The adoption rate of a network also tends to increase in proportion to the utility provided by the network, which is why companies often give away software or other products for free in order to increase the size of their user base and the value of their network.

Metcalfe's law is often cited as a factor that can contribute to the emergence of scale-free, or power law, distributions in networks. This type of distribution is characterized by a few nodes (or users) with many connections, and many nodes with only a few connections. The existence of network effects, in which the value of a network increases with the number of users, can help to explain why we don't see many Facebooks or Googles – it can be difficult for new networks to gain traction and achieve the same level of utility as established networks with a large user base.

### Security Topics for Distributed Systems

Security is an important concern in distributed systems, as they often handle sensitive data or perform critical functions. Some key security topics that are relevant to distributed systems include:

- **Authentication**: This refers to the process of verifying the identity of a user or device. In a distributed system, authentication may be used to ensure that only authorized users can access certain resources or perform certain actions.
- **Authorization**: This refers to the process of granting or denying access to specific resources or actions based on the identity of a user or device. In a distributed system, authorization controls may be used to ensure that users can only perform actions that are appropriate for their role or level of access.
- **Confidentiality**: This refers to the protection of information from unauthorized access or disclosure. In a distributed system, confidentiality may be achieved through techniques such as encryption or the use of secure channels for communication.
- **Integrity**: This refers to the protection of information from unauthorized modification or tampering. In a distributed system, integrity may be maintained through techniques such as hashing or the use of digital signatures.
- **Non-repudiation**: This refers to the ability to prove that a specific action or transaction was performed by a particular user or device. In a distributed system, non-repudiation may be achieved through techniques such as digital signatures or the use of timestamps.
- **Privacy/anonymity**: These refer to the protection of personal information and the ability to use a system without revealing one's identity. In a distributed system, privacy and anonymity may be achieved through techniques such as the use of pseudonymous identities or the use of encryption to protect communications.
- **Firewalls**: A firewall is a security system that controls incoming and outgoing network traffic based on predetermined security rules. In a distributed system, firewalls can be used to protect against unauthorized access and to prevent malicious traffic from entering or leaving the system.
- **Certificates, public key infrastructure (PKI), and digital signatures**: These are tools and techniques that are used to establish trust and authentication in a distributed system. Certificates, for example, can be used to verify the identity of a user or device, while PKI is a system that manages the issuance and revocation of certificates. Digital signatures are used to verify the authenticity of a message or document.
- **Encryption**: Encryption is a technique that is used to protect information from unauthorized access or disclosure. In a distributed system, encryption can be used to secure communication channels and to protect data at rest. There are a variety of encryption methods and devices that can be used to achieve this goal.
- **Software architecture**: The design and organization of the software components in a distributed system can have a significant impact on its security. It is important to consider security throughout the software development process and to design the system with security in mind.
- **Intrusion detection**: This refers to the process of identifying and responding to unauthorized access or activity in a distributed system. Intrusion detection systems are used to monitor the system for signs of an attack or other security breach, and to alert administrators or take other appropriate action when an incident is detected.
- **Sniffing**: This refers to the practice of intercepting and monitoring network traffic in order to gather information or to perform other malicious actions. In a distributed system, sniffing can be used to capture sensitive data or to disrupt communication.
- **PGP, SSL, etc.**: These are tools and protocols that are used to secure communication in a distributed system. PGP (Pretty Good Privacy) is a data encryption and decryption program, while SSL (Secure Sockets Layer) is a protocol for establishing secure links between networked
- **Denial of service (DoS) attacks**: These are attacks that are designed to disrupt the availability of a network or system by flooding it with traffic or other requests, thereby preventing legitimate users from accessing the system. In a distributed system, DoS attacks can be particularly disruptive as they can affect multiple components at once.

### Theoretical Foundations of Distributed Systems

The theoretical foundations of distributed systems are a set of concepts and principles that form the basis for the design and analysis of these systems. Some of the key theoretical foundations of distributed systems include:

- **No global time**: In a distributed system, it is not possible to rely on a single, global clock to coordinate events. Instead, techniques such as logical clocks and vector clocks are used to provide a partial ordering of events within the system.
- **FLP theorem of asynchronous systems**: The FLP (Fischer, Lynch, and Patterson) theorem states that it is impossible to design an asynchronous distributed system that is both safe and live (that is, capable of making progress). This theorem highlights the challenges of building distributed systems that can handle failures or delays in communication.
- **Failure detection and timeout**: One of the challenges of distributed systems is detecting failures or delays in communication and deciding how to respond to them. Timeout mechanisms are often used to detect failures, but setting appropriate timeout values can be difficult.
- **Concurrency and deadlocks**: In a distributed system, multiple processes may execute concurrently, which can lead to situations where two or more processes are waiting for each other to complete before they can make progress. This is known as a deadlock, and can be difficult to resolve in a distributed system.
- **CAP theorem**: The CAP (consistency, availability, partitioning) theorem states that it is impossible for a distributed system to simultaneously provide all three of the following properties: consistency, availability, and partition tolerance. This theorem highlights the trade-offs that must be made when designing a distributed system.
- **End-to-end argument**: The end-to-end argument states that certain functions should be placed at the endpoints of a system, rather than in the middle, in order to maximize flexibility and modularity. This principle is often applied in distributed systems to determine where certain functions should be implemented.
- **Consensus, leader selection, etc.**: Consensus is the process of agreeing on a single value or decision in a distributed system. This can be challenging in the presence of failures or delays, and requires mechanisms such as leader selection or voting to resolve.

### Distributed Systems Design Fields

The design of a distributed system involves addressing a number of common problems and considering various architectural factors in order to create a system that is scalable, reliable, and secure. Some key considerations in distributed system design include:

- **Common problems**: When designing a distributed system, it is important to consider a number of common problems that can impact the performance, reliability, and security of the system. These include issues such as fail-over, maintenance, policies, and security integration.
- **Information architecture**: The information architecture of a distributed system refers to the way in which information is organized and structured within the system. This includes defining and qualifying the various information fragments and flows that make up the system.
- **Distribution architecture**: The distribution architecture of a distributed system refers to the layout and organization of the various components of the system and how they are connected to each other. This includes creating a map of all participating systems and their quality of service, and determining how communication and resource sharing will be managed within the system.

### An Introduction to Middleware

Middleware is software that sits between the operating system and the application layer of a distributed system, providing a layer of abstraction that enables communication and resource sharing among the various components of the system. Some key characteristics of middleware include:

- It is used to facilitate the creation of distributed applications.
- Provides glue code and generators that allow different programming languages and systems to interoperate.
- Controls messages and enforces delivery guarantees, such as at-least-once delivery.
- Reorders requests from participants to create a causal or total ordering.
- Takes over responsibility for messages and may store them temporarily.
- Creates groups of nodes that process events together and controls fail-over.
- Hides differences in hardware, location of services, and offers load balancing.
- Allows filtering of requests or provides means to add additional security information to calls.
- Provides powerful services such as locking, scheduling, and messaging to applications.
- Offers frameworks that provide automatic storage, security checks, and transactional control.
- Supports message bus architectures that provide loose coupling through publish/subscribe functions.

The importance of middleware in distributed systems cannot be overstated. It is essential for enabling communication and resource sharing among the various components of the system, and for abstracting away the complexities of working with distributed systems. Without middleware, it would be much more difficult to develop distributed applications that are scalable, reliable, and secure.

### Distribution Transparencies

Distribution transparencies are features that are designed to hide the complexities of working with distributed systems from the user or developer. Some key distribution transparencies include:

- **Access**: This transparency masks differences in languages and data representation, allowing different systems to communicate and exchange data with each other.
- **Failure**: This transparency masks failures and enables fault tolerance through automated fail-over to other servers.
- **Scalability**: This transparency provides intelligent load balancing of requests to ensure that the system can handle a large number of requests without becoming overloaded.
- **Redundancy**: This transparency transparently replicates data to ensure that it is available even if one or more servers fail.
- **Location**: This transparency allows users to access services using logical, rather than physical, names. This enables services to be moved or relocated without affecting the user experience.
- **Migration**: This transparency hides the true location of a service or object from clients. If the location changes, the client will not notice.
- **Persistence**: This transparency automatically loads and stores data on demand to unload server memory.
- **Sharding**: This transparency distributes storage requests across multiple backend systems to ensure that the system can scale to handle a large volume of data.
- **Transactions**: This transparency makes requests ACID (Atomic, Consistent, Isolated, and Durable), ensuring that they are executed correctly and consistently.
- **Security**: This transparency automatically checks for the required credentials or roles in requests, ensuring that only authorized users can access resources.
- **Monitoring**: This transparency creates central logs with correlation IDs that join request parts across nodes, enabling administrators to track and monitor the performance of the system.

### Classification of Middleware

Middleware can be classified into several categories based on the type of service it provides and the way it communicates with other components in a distributed system. Some common types of middleware include:

- **Socket-based services**: These are middleware systems that use sockets to communicate with other components in a distributed system. Sockets are a low-level communication mechanism that allows programs to send and receive data over a network.
- **Remote procedure calls (RPCs)**: These are middleware systems that allow programs to make calls to procedures or functions that are located on a remote machine, as if they were located on the local machine.
- **Object request brokers (ORBs)**: These are middleware systems that enable communication between objects that are running on different machines. ORBs provide an interface that allows objects to communicate with each other using a common protocol. Examples include CORBA and RMI.
- **Message-oriented middleware (MOMs)**: These are middleware systems that enable communication between components by exchanging messages. MOMs are often used in event-driven systems and reactive systems, which respond to external events or stimuli.
- **Web services**: These are middleware systems that provide a way for different applications to communicate over the web using standard protocols such as XML-RPC, SOAP, and UDDI. Web services are often used in service-oriented architectures (SOA) and representational state transfer (REST) systems.
- **Frameworks**: These are middleware systems that provide a set of tools and libraries for building distributed applications. Examples include Enterprise Java Beans (EJBs) and the Java 2 Enterprise Edition (J2EE).
- **Peer-to-peer (P2P) systems**: These are middleware systems that enable communication and resource sharing among a group of computers or devices that are connected to each other. P2P systems do not rely on a central server, but rather allow each device to communicate directly with other devices in the network.
- **Agent-based systems**: These are middleware systems that use software agents to communicate with other components in a distributed system. Agents are autonomous programs that are designed to perform a specific task or function. Examples include Jini and Aglets.
- **Tuple-spaces and distributed blackboards**: These are middleware systems that use a shared memory space to enable communication and resource sharing among different components in a distributed system.
- **Warehouse-computing architectures**: These are middleware systems that are designed to support the storage and processing of large volumes of data in a distributed environment, such as a data center.

## Theoretical Models of Distributed Systems

### Overview

1. Message passing theoretical model
2. Distributed computing topologies
3. Client-server systems, including critical points, architectures, processing and I/O models

### Synchronous vs. Asynchronous Systems

Synchronous and asynchronous systems are two types of distributed systems that differ in the way that they handle communication and the passage of time.

In a **synchronous system**, events are assumed to be delivered in a lockstep manner, with a fixed delay between the occurrence of an event and its delivery. This means that events are delivered at predetermined intervals, and the system can be designed to operate on the assumption that events will be delivered at these intervals.

**Asynchronous systems** do not have a fixed delay between the occurrence of an event and its delivery. Events may be delivered at any time, and the system must be able to handle this uncertainty. Asynchronous systems typically require more complex distributed algorithms to ensure correct operation, but they are generally easier to build and maintain than synchronous systems.

In practice, most distributed systems are asynchronous, with additional mechanisms such as failure detectors and randomization used to help ensure correct operation.

### Properties of Message Protocols

Message protocol properties are characteristics that describe the desired behavior of a message passing protocol in a distributed system. These properties are used to ensure that the protocol operates correctly and achieves its intended goals.

Some common message protocol properties include:

- **Correctness**: This property refers to the invariant properties of the protocol, which are properties that are expected to hold throughout all possible executions of the protocol. Ensuring the correctness of a protocol is important for ensuring that the protocol achieves its intended goals.
- **Liveness/termination**: This property refers to the ability of the protocol to make progress in the context of certain failures and within a bounded number of rounds. A protocol that satisfies this property is said to be "lively" or "live", while a protocol that does not satisfy this property is said to be "deadlock".
- **Fairness**: This property refers to the inability of any participant in the protocol to be "starved" or denied access to resources. A protocol that satisfies this property is said to be "fair", while a protocol that does not satisfy this property is said to be "unfair".
- **Agreement**: This property refers to the ability of all participants in the protocol to agree on a specific decision or output value. Ensuring agreement is important for ensuring that the protocol achieves a consistent result.
- **Validity**: This property refers to the ability of the protocol to output a result that is consistent with the input value. A protocol that satisfies this property is said to be "valid", while a protocol that does not satisfy this property is said to be "invalid".

### Complexity of Distributed Algorithms

- **Time complexity** refers to the amount of time it takes for an algorithm to complete. This is often measured in terms of the time of the last event before all processes finish.
- **Message complexity** refers to the number of messages that need to be sent in order for the algorithm to complete. This includes both the number of messages sent and the size of the messages. The number of rounds needed for termination is also an important factor in the message complexity of an algorithm, as it can have a significant impact on the overall scalability of the protocol.

### Failure Types

In distributed systems, there are several types of failures that can occur. These failures can have different impacts on the system and can require different approaches to handling them.

Some common types of failures in distributed systems include:

- **Crash failure**: This type of failure occurs when a process stops working and remains down. This can be caused by a variety of issues, such as hardware or software problems.
- **Connectivity failures**: This type of failure occurs when there is a problem with the network that connects the nodes in the system. This can cause "split brain" situations, where the system becomes divided into two separate networks, or node isolation, where a node becomes disconnected from the rest of the system.
- **Message loss**: This type of failure occurs when individual messages are lost during transmission. This can be caused by a variety of issues, such as network problems or hardware failures.
- **Byzantine failures**: This type of failure occurs when nodes in the system violate protocol assumptions and promises. This can include breaking promises due to disk or configuration failures, or intentionally behaving in a way that goes against the protocol. Byzantine failures are often considered to be the most difficult type of failure to handle in a distributed system, as they can be difficult to detect and can have significant impacts on the system.

### Distributed Computing Topologies

There are several types of distributed computing topologies that can be used to design distributed systems. These topologies can have different characteristics and can be used to achieve different goals, depending on the needs of the system.

Some common types of distributed computing topologies include:

- **Client/server systems**: In this type of topology, clients initiate communication with servers, which process the requests and send a response back to the client. This is the most common type of distributed system and is often used for applications where clients need to request specific information or services from servers.
- **Hierarchical systems**: In this type of topology, every node can act as both a client and a server, but some nodes may play a special role, such as a domain name system (DNS) server. This type of topology can reduce communication overhead and provide options for central control, making it useful in certain types of systems.
- **Totally distributed systems**: In this type of topology, every node is both a client and a server. This type of topology can be useful for systems where nodes need to communicate with each other directly, rather than relying on a central server.
- **Bus systems/pub-sub**: In this type of topology, every node listens for data and posts data in response. This can be useful for event-driven systems where nodes need to communicate with each other asynchronously.

### Queuing Theory: Kendall Notation M/M/m/ß/N/Q

The Kendall notation, also known as the Kendall notation for Markov chains, is a way of describing the behavior of a queuing system. It is often used in the field of operations research to analyze the performance of systems that have a finite number of servers and a finite queue size.

- `ß`: Population Size (limited or infinite)
- `M,D,G`: Probability distribution for arrivals
- `N`: Wait queue size (can be unlimited)
- `Q`: Service policy type (Fifo, shortest remaining time first etc)
- `M,D,G`: Probability distribution for service time
- `m`: Number of service channels

### Generalized Queuing Theory Terms (Henry Liu)

- **Server/Node**: A combination of a wait queue and a processing element
- **Initiator**: The entity that initiates a service request
- **Wait time**: The time a request or initiator spends waiting in line for service
- **Service time**: The time it takes for the processing element to complete a request
- **Arrival rate**: The rate at which requests arrive for service
- **Utilization**: The percentage of time the processing element spends servicing requests, as opposed to being idle
- **Queue length**: The total number of requests waiting and being serviced
- **Response time**: The sum of the wait time and service time for a single visit to the processing element
- **Residence time**: The total time spent by the processing element on a single transaction, if it is visited multiple times
- **Throughput**: The rate at which requests are serviced, or how fast requests can be processed without long wait times.

### Little's Law

- Little's Law states that in a stable system, the long-term average number of customers (L) is equal to the long-term average effective arrival rate (λ) multiplied by the average time a customer spends in the system (W).
- This can be expressed algebraically as L = λW.
- Little's Law is used to analyze and understand the behavior of systems that involve waiting, such as queues or lines. It can help to predict the average number of customers in a system, as well as the average time they will spend waiting, given a certain arrival rate.

### Hejunka

Hejunka is a Japanese term that refers to the practice of leveling the production process by smoothing out fluctuations in demand and task sizes. It is often used in lean manufacturing and just-in-time (JIT) production systems to improve the efficiency and flow of work through a system.

The goal of Hejunka is to create a steady, predictable flow of work through the system by reducing variability in task sizes and demand. This can be achieved through a variety of methods, such as:

- **Setting limits** on the number of tasks or requests that can be processed at any given time
- **Balancing the workload** across different servers or processing elements
- **Prioritizing tasks** based on their importance or impact on the overall system
- Using techniques such as **batching or grouping** similar tasks together to reduce variability

By leveling the production process and reducing variability in task sizes, Hejunka can help to improve the efficiency and flow of work through a system, and reduce the risk of bottlenecks or delays caused by large differences in task size.

### Lessons Learned from Queuing Theory

- **Request numbers**: Caching can be used to reduce the number of requests that need to be processed by storing frequently accessed data in memory, so that it can be quickly retrieved without the need to fetch it from a slower storage medium.
- **Batching**: The use of a multi-get API can help to reduce the number of requests that need to be processed by allowing multiple requests to be bundled together and processed as a single unit.
- **Task sizes and variability**: Service level agreements (SLAs) can be used to define the acceptable level of variability in task sizes and completion times, and Hejunka is a technique that involves leveling the production process by smoothing out fluctuations in demand and task sizes. This can help to reduce variability and improve the efficiency of the system.

### Request Problem in Multi-Tier Networks

In a multi-tier network, the request problem refers to the fact that **requests must travel through multiple layers or tiers of servers** in order to be processed, and each layer adds its own processing time and potential delays to the overall response time.

The average response time in a multi-tier network is therefore the sum of the trip average (the time it takes for a request to travel from one server to the next) multiplied by the wait time (the time a request spends waiting for a server to become available) at each layer, plus the sum of the service demand (the time it takes for a server to process a request) at each layer.

It is important to note that in a multi-tier network, all requests are synchronous and may be in contention with each other, which means that wait times can occur due to contention for server resources. This can impact the overall efficiency of the system and may require the use of techniques such as caching or batching to reduce the number of requests that need to be processed.

### Task Size Problem in Multi-Tier Networks

In a multi-tier network, the task size problem refers to the fact that differences in task size can cause delays and inefficiencies in the processing of requests.

In the case of pipeline stalls between nodes, large differences in task size can cause requests to be held up at one node while waiting for the next node to become available, leading to delays in the overall response time.

### Theories & Model vs. Reality

When applying queuing theory models to real-world systems, there are several factors that can impact the accuracy and usefulness of the model. These include:

- **Latency**: Latency refers to the time it takes for a request to travel from one server to another or for a task to be completed. Latency can vary based on a variety of factors, such as network speed, server load, and the distance between servers, and it can impact the accuracy of queuing theory models.
- **Blocking/locking/serialization in service units**: In real-world systems, servers may block or lock requests while they are being processed, or may process requests serially rather than in parallel. This can impact the accuracy of queuing theory models that assume parallel processing.
- **Non-random distributions and feedback effects**: In real-world systems, request and task arrival rates may not always follow a random distribution, and there may be feedback effects that impact the flow of work through the system. This can make it difficult to accurately model the behavior of the system using queuing theory.
- **Dead requests**: In some cases, requests may be lost or dropped due to errors or other issues, which can impact the accuracy of queuing theory models.
- **Backpressure**: In systems where the capacity of servers or processing elements is limited, it is possible for requests to build up and create a backlog of work. This is known as backpressure, and it can impact the accuracy of queuing theory models.
- **Missing variables and coherence losses**: Queuing theory models may not always include all the relevant variables or may not accurately account for coherence losses, which can impact their accuracy in predicting the behavior of real-world systems.

### Critical Points in Client/Server Systems

On the **client side**:

- **Locating the server**: The client must be able to locate the server in order to establish a connection. This process can be impacted by factors such as network speed and latency.
- **Authentication**: The client may need to authenticate itself in order to access the server and its resources.
- **Sync/async**: The client may be able to send requests synchronously or asynchronously, which can impact the overall performance of the system.
- **Speed up/down**: The client may be able to adjust the speed at which it sends requests in order to optimize the performance of the system.
- **Load balancing**: The client may need to use load balancing techniques to distribute requests evenly across multiple servers or processing elements.
- **Queues**: The client may need to use queues to manage requests and ensure that they are processed in an orderly manner.

On the **server side**:

- **Many clients**: The server may need to handle requests from many clients simultaneously, which can impact its performance and efficiency.
- **Session state**: The server may need to maintain session state information in order to track the progress of individual requests.
- **Authentication**: The server may need to authenticate clients
- **Authorization**: The server may need to authorize clients to access specific resources or perform certain actions.
- **Privacy**: The server may need to ensure that client data is kept private and secure.
- **Sync/async**: The server may be able to process requests synchronously or asynchronously, which can impact the overall performance of the system.
- **Blocking**: The server may block requests while they are being processed, which can impact the performance of the system.
- **Single/multicore CPU intensive**: The server may be able to use multiple cores or processors to process requests in parallel, or it may be limited to processing requests serially on a single core.
- **Queues**: The server may need to use queues to manage requests and ensure that they are processed in an orderly manner.

Between both: **Bandwidth/latency**; The bandwidth and latency of the network connection between the client and the server can impact the performance and efficiency of the system.

### Stateful vs Stateless Systems (The Stateful Server Problem)

The stateful server problem refers to the trade-offs that must be considered when designing and implementing a server-based system that maintains state information.

On the one hand, stateful servers have several **advantages**:

- **Data locality**: Stateful servers can store data locally, which can improve the performance of the system by reducing the need to fetch data from external storage.
- **Consistency**: Stateful servers can ensure that data is consistent and up-to-date, which can be important in certain applications.

However, stateful servers also have some **disadvantages**:

- **Availability**: Stateful servers may be less available than stateless servers, as they may be more vulnerable to failures or downtime.
- **Load balancing**: Stateful servers may be more difficult to load balance than stateless servers, as they must maintain state information for individual clients.

Stateless design, on the other hand, stores all data in external storage such as databases or caches, which can make it easier to design and implement the system. However, in the event of failures, programming stateless systems can be more difficult, as all data must be retrieved from external storage.

### Terminology for Client/Server Systems

- **Host**: A physical machine with n CPUs.
- **Server**: A process running on a host that receives messages, performs computations, and sends messages (not necessarily responses).
- **Thread**: An independent computation context within a process, which can be pre-empted by the kernel (kernel-thread) or yield voluntarily (application-level scheduling).
- **Multi-threading**: The use of multiple threads within a single process context. This can be achieved using kernel-level threading (where the kernel switches between threads) or using multiple kernel threads running in parallel on a multi-core system.
- **Multi-channel**: A thread that is able to watch multiple channels using a single system call, such as a `select()` call.
- **Synchronous processing**: A caller calls a function and waits for its results, doing nothing while waiting.
- **Asynchronous processing**: A caller calls a function and immediately continues executing its own code. The called function is eventually executed, and a callback function is called to inform the caller about the completion.
- **Parallel processing**: The deterministic execution of independent code paths.
- **Blocking**: A thread calls a function that needs time to complete, such as fetching a resource from disk. The thread cannot continue and blocks an execution core while waiting for the result. The thread is "context switched" and a new code path is loaded and executed by the core.
- **Non-blocking calls**: A caller calls the non-blocking version of a function. If the function can perform immediately without delaying the caller, it will do so. If the function needed time to perform its job, it will allow the caller to return immediately and inform it that it would be blocked. The caller can then decide to do something else and try again later (poll again).
- **Synchronization**: The control of access to shared data by multiple threads in order to prevent data inconsistencies.

### Overarching Client/Server Architectures

- **Multi-Tier System**: This type of architecture involves splitting up the system into multiple layers or tiers, each of which performs a specific set of functions. The tiers may include a presentation layer, a business logic layer, and a data storage layer, among others.
- **Large fan-out Architectures**: This type of architecture involves a central component that receives requests from many clients and distributes them to multiple servers or other resources. This can allow the system to scale more easily and handle a large volume of requests.
- **Pipeline (SEDA)**: This type of architecture involves breaking up the processing of a request into multiple stages, each of which is handled by a separate component. The stages are connected in a pipeline, with each stage processing the request and passing it on to the next stage.
- **Offline Processing**: This type of architecture involves processing requests and tasks in an offline or deferred manner, rather than in real-time. This can be useful in situations where the workload is too large to handle in real-time, or where real-time processing is not required.

### Different Process Models

- **Single Thread/Single Core**: This type of process model involves a single thread of execution running on a single core. This can be efficient for certain types of workloads, but may not be able to take full advantage of multiple cores or processors.
- **Multi-Thread/Single Core**: This type of process model involves multiple threads of execution running on a single core. This can allow the system to perform multiple tasks concurrently, but may not be able to fully utilize the processing power of multiple cores or processors.
- **Multi-Thread/Multi-Core**: This type of process model involves multiple threads of execution running on multiple cores or processors. This can allow the system to fully utilize the processing power of multiple cores or processors, and can be more efficient for certain types of workloads.
- **Single Thread/Multi-Process**: This type of process model involves a single thread of execution running within each of multiple processes. This can allow the system to take advantage of multiple cores or processors, but may be less efficient than other models for certain types of workloads.

### Questions for Process Models

- Can it use available cores/CPUs?
- What is the ideal number of threads?
- How does it deal with delays/(b)locking?
- How does it deal with slow requests/uploads?
- Is there observable non-determinism aka race conditions?
- Is locking/synchronization needed?
- What is the overhead of context switches and memory?

### Amdahl's Law

According to Amdahl's Law, the maximum improvement in overall system performance that can be achieved by improving a particular part of the system is limited by the fraction of time that the improved part of the system is used. In other words, if only a small portion of the system's workload is affected by the improvement, the overall improvement in performance will also be small.

$speedup = \frac{1}{(1-parallelfraction+\frac{parallelfraction}{numberofprocessors}}$

For example, if a particular part of a system is improved so that it runs twice as fast, but that part of the system is only used 10% of the time, the overall improvement in system performance will be limited to a 10% increase. On the other hand, if the improved part of the system is used 50% of the time, the overall improvement in performance will be much larger, at 50%.

Amdahl's Law is often used to understand the potential benefits and limitations of optimizing or improving specific parts of a system. It can be a useful tool for determining how much resources should be invested in improving a particular part of the system, and for understanding the potential impact of those improvements on overall system performance.

### Different I/O Models

- **Java before NIO/AIO**: Prior to the introduction of the Java New I/O (NIO) and Asynchronous I/O (AIO) APIs, Java had a different model for handling input/output (I/O) operations. This model involved using threads to block and wait for I/O operations to complete, which could be inefficient and consume a lot of system resources.
- **Polling pattern**: The polling pattern is a way of handling I/O operations in which a central component periodically checks for the completion of I/O operations. This can be done by repeatedly calling a function that checks the status of the operation, or by using a timer to trigger the check at regular intervals.
- **Reactor pattern**: The Reactor pattern is a way of handling I/O operations in which a central component is notified when an I/O operation is completed, rather than periodically checking for its completion. This can be more efficient than the polling pattern, as it allows the system to respond to I/O operations as soon as they are completed, rather than waiting for a periodic check.
- **Proactor pattern**: The Proactor pattern is similar to the Reactor pattern, but it is designed to handle high-concurrency environments where many I/O operations are occurring simultaneously. It uses a combination of asynchronous I/O and event-driven design to allow for efficient handling of multiple I/O operations at once.

### Questions for I/O Models

- Can it deal with all kinds of input/output?
- How are synchronous channels integrated?
- How hard is programming?
- Can it be combined with multi-cores?
- Scalability through multi-processes?
- Race conditions possible?

## Message Protocols

### Overview

1. Message protocols
   1. Delivery guarantees in point-to-point communication
   2. Reliable broadcast
   3. Request ordering and causality
2. Programming client-server systems using sockets

### The Role of Delivery Guarantees

**Shop order**: The scenario described involves an online shop in which orders are placed and processed. The goal is to ensure that orders are delivered correctly and efficiently, regardless of any potential issues that may arise.

- **TCP Communication properties**: TCP (Transmission Control Protocol) is a networking protocol that is used to establish and maintain communication between devices over a network. It has several key properties that are relevant to the scenario described, including reliability, flow control, and congestion control.
- **At-least-once**: The "at-least-once" delivery guarantee means that a message may be delivered more than once, but it will always be delivered at least once. This can be useful in situations where it is more important to ensure that a message is delivered, even if it may be duplicated, than it is to prevent duplicates from occurring.
- **At-most-once**: The "at-most-once" delivery guarantee means that a message will be delivered at most once. This can be useful in situations where it is more important to prevent duplicates from occurring than it is to ensure that a message is always delivered.
- **Exactly once**: The "exactly once" delivery guarantee means that a message will be delivered exactly once, with no duplicates. This can be more difficult to achieve than the other delivery guarantees, as it requires additional complexity and overhead to ensure that duplicates are prevented.
- **Message complexity**: The number of messages sent refers to the total number of messages that are transmitted as part of the communication process. In the scenario described, the number of messages sent may affect the efficiency and reliability of the communication process, and may need to be taken into account when determining the appropriate delivery guarantee to use.

### Why is TCP not Enough?

While TCP (Transmission Control Protocol) is a widely used networking protocol that provides a reliable communication channel between devices, it is not always sufficient on its own to ensure proper behavior in all situations. Here are some reasons why TCP may not be enough:

- **Lost messages retransmitted**: TCP includes mechanisms for retransmitting lost messages, which can help to improve the reliability of communication. However, if messages are frequently lost or the network is particularly unreliable, the overhead of retransmitting lost messages may become a burden on the system.
- **Re-sequencing of out of order messages**: TCP includes mechanisms for reordering out-of-order messages, which can help to ensure that messages are delivered in the correct order. However, if messages are frequently delivered out of order, this can be inefficient and may cause issues with the overall communication process.
- **Sender choke back (flow control)**: TCP includes flow control mechanisms that allow the sender to adjust its rate of transmission based on the capacity of the receiver. However, if the sender is sending messages too quickly, this can lead to congestion on the network and reduced performance.
- **No message boundary protection**: TCP does not provide any protection for message boundaries, which means that messages may be broken up or combined during transmission. This can make it difficult to ensure that messages are delivered in their entirety and can cause issues with the overall communication process.
- **Timeout problem**: TCP includes mechanisms for detecting and handling connection failures, but these mechanisms may not be sufficient in all situations. For example, if a connection is lost due to a timeout, it may take some time to detect and recover from the failure, which can lead to delays and disruptions in the communication process.

To address these and other issues, it may be necessary to use additional protocols or techniques, such as message-oriented middleware or application-level protocols, to ensure proper behavior in case of connection failures and to provide additional features and guarantees for message delivery.

### Different Levels of Timeouts

- **Business-Process-Timeout**: This timeout is set at the business process level and is used to ensure that a business process does not get stuck or take too long to complete. This timeout may be triggered if a particular task or operation within the process takes longer than expected to complete, or if the process as a whole takes too long to finish.
- **RPC-Timeout (order progress)**: This timeout is set at the level of remote procedure calls (RPCs) and is used to ensure that RPCs do not get stuck or take too long to complete. This timeout may be triggered if an RPC takes longer than expected to complete, or if the progress of an RPC is not being monitored properly.
- **TCP-Timeout (reliable channel)**: This timeout is set at the TCP (Transmission Control Protocol) level and is used to ensure that the reliable communication channel provided by TCP is functioning properly. This timeout may be triggered if a connection is lost or if the channel becomes congested or otherwise unstable.

### Delivery Guarantees for RPCs

- **Best effort**: The "best effort" delivery guarantee means that no specific guarantees are made about the delivery of requests or responses. This means that requests may be lost or responses may not be received, and there is no mechanism in place to ensure that this does not happen.
- **At least once**: The "at least once" delivery guarantee means that a request may be delivered more than once, but it will always be delivered at least once. This can be useful in situations where it is more important to ensure that a request is delivered, even if it may be duplicated, than it is to prevent duplicates from occurring.
- **At most once**: The "at most once" delivery guarantee means that a request will be delivered at most once. This can be useful in situations where it is more important to prevent duplicates from occurring than it is to ensure that a request is always delivered.
- **Once and only once/exactly once**: The "once and only once" or "exactly once" delivery guarantee means that a request will be delivered exactly once, with no duplicates. This can be more difficult to achieve than the other delivery guarantees, as it requires additional complexity and overhead to ensure that duplicates are prevented.

### Idempotency

Idempotency is a property of operations or requests that ensures that they can be safely repeated without changing the result of the operation. In other words, if an operation is idempotent, it will have the same result whether it is performed once or multiple times.

- The first request needs to be idempotent: In a sequence of requests, it is important that the first request is idempotent. This ensures that the first request can be safely repeated if it fails or is lost, without affecting the overall result of the operation.
- The last request can be only best effort
- Messages may be reordered

### Server State and Idempotency

Idempotency is an important property to consider when designing operations or requests that may be repeated or delivered multiple times, as it can help to ensure that the operation or request is able to be safely repeated without affecting the overall result. Here are some additional considerations related to idempotency and server state:

- **No need to remember a request and its result**: If an operation or request is idempotent, the server does not need to remember the request or its result. This can be useful in situations where the server's storage is limited or unreliable, as it means that the server does not need to maintain a record of all previous requests and their results.
- **Server can lose its storage**: If the server's storage is lost or becomes unavailable, it should not affect the overall result of the operation or request, as long as the operation or request is idempotent. This can help to ensure that the operation or request is able to be safely repeated even if the server's storage is lost.
- **Concurrent updates might be consistent without concurrency control**: If an operation or request is idempotent, it is possible that concurrent updates to the same data may be consistent without the need for concurrency control mechanisms such as locks or transactions. This can help to improve the efficiency and performance of the system.

### Implementing Delivery Guarantees for Idempotent Requests

- **"At least once"** implementation for idempotent requests: For idempotent requests, the "at least once" delivery guarantee can be implemented by simply sending an acknowledgement (ack) to the client after the request has been received. This approach does not require any updates to the server state, and is suitable for requests that do not have any critical side effects.
- **"At most once"** implementation for nonidempotent requests: For nonidempotent requests, the "at most once" delivery guarantee can be implemented by storing a response on the server until the client confirms that it has been received. This approach requires the server to maintain state for each response, and may involve adding a request number to each request to help the server detect and discard duplicate requests.
- **"Exactly once"** implementation: The "exactly once" delivery guarantee is not possible to achieve in asynchronous systems with network failures. However, it can be approximated using techniques such as two-phase commit and epoch numbers, which allow the client and server to coordinate their actions and ensure that they do not forget their decisions. This approach may involve maintaining an atomic log on both the client and server, and storing responses on the server until they are confirmed by the client

### Repeating Non-Idempotent Operations

If an operation is not idempotent, it means that it cannot be safely repeated multiple times and is likely to have unintended side effects. In this case, there are several measures that can be taken to ensure reliable communication:

- **Use a message ID** to filter for duplicate sends: By including a unique message ID in each request, the server can filter out duplicates and only execute the request once.
- **Keep a history list of request execution results** on the server: If the reply to a request is lost, the server can retransmit the result from its history list. This helps to ensure that the client receives the correct result even if the initial reply was lost.
- **Lease resources on the server**: In some cases, it may be necessary to keep state on the server in order to facilitate communication. For example, a client may "lease" resources on the server for a specific period of time. This can help to ensure that resources are used efficiently and released when they are no longer needed.

It is important to carefully manage state on the server in order to avoid overloading the system with old replies. It may be necessary to set limits on how long to store old replies and when to discard them.

### Request Order in Multi-Point-Protocols

- **No request order from one sender**: In a multi-point protocol, there is no guaranteed order for requests sent by a single sender. This means that requests may be received and processed in a different order than they were sent, and the sender should be prepared to handle this possibility.
- **No request order between different senders**: In a multi-point protocol, there is no guaranteed order for requests sent by different senders. This means that requests from different senders may be received and processed in a different order than they were sent, and the senders should be prepared to handle this possibility.
- **No request order between independent requests of different senders**: In a multi-point protocol, there is no guaranteed order for independent requests sent by different senders. This means that independent requests from different senders may be received and processed in a different order than they were sent, and the senders should be prepared to handle this possibility.

### Request Ordering with Multiple Nodes

In a multi-node system, it may be necessary to use a reliable broadcast protocol to ensure that requests are processed in the desired order. Here are some examples of protocols that can be used for request ordering with multiple nodes:

- **Reliable Broadcast**: Reliable broadcast is a protocol that ensures that a message is delivered to all nodes in the system, and that it is delivered in the same order to all nodes. This can help to ensure that requests are processed in the correct order, even if they are sent from different nodes or if there are delays or other issues with the network.
- **FIFO Cast**: FIFO cast is a protocol that ensures that messages are delivered in the order in which they were sent, with the first message sent being the first one to be delivered. This can help to ensure that requests are processed in the correct order, even if they are sent from different nodes or if there are delays or other issues with the network. This can still lead to causal inconsistencies!
- **Causal Cast**: Causal cast is a protocol that ensures that messages are delivered in a causally consistent order, based on the dependencies between the messages. This can help to ensure that requests are processed in the correct order, even if they are sent from different nodes or if there are delays or other issues with the network.
- **Absolutely Ordered Casts**: Absolutely ordered casts is a protocol that ensures that messages are delivered in a totally ordered sequence, with no uncertainty about the order in which the messages were sent. This can help to ensure that requests are processed in the correct order, even if they are sent from different nodes or if there are delays or other issues with the network.

### Implementing Causal Ordered Broadcasts

- **Piggybacking previous messages**: One solution for implementing causal ordered broadcasts is to piggyback every message sent with the previous messages. This means that when a message is sent, it is accompanied by the previous messages that it depends on. This can help to ensure that processes that may have missed a message can learn about it with the next incoming message and then deliver it correctly.
- **Sending event history with every message**: Another solution for implementing causal ordered broadcasts is to send the event history with every message. This can be done using techniques such as vector clocks, which are used to track the dependencies between events in a distributed system. With this approach, messages are not delivered until the order is correct. This can help to ensure that messages are delivered in the correct order, even if there are delays or other issues with the network.

### Implementing Absolutely Ordered Casts

- **All nodes send messages to every other node**: One solution for implementing atomic broadcasts is for all nodes to send their messages to every other node in the system. This ensures that all nodes have a complete set of messages, which can be used to determine the total order of the messages.
- **All nodes receive messages, but wait with delivery**: After receiving all of the messages, all nodes can wait with delivery until the total order of the messages has been determined.
- **One node is selected to organize the total order**: To determine the total order of the messages, one node can be selected to organize the messages into a total order. This node can use a variety of techniques, such as vector clocks or Lamport timestamps, to determine the order of the messages.
- **The node sends the total order to all nodes**: Once the total order has been determined, the node can send the total order to all other nodes in the system.
- **All nodes receive the total order and deliver their messages**: Finally, all nodes can receive the total order and deliver their messages according to the determined order.

There are however disadvantages with these implementations:

- **May have high overhead**: This solution may have high overhead, as it requires all nodes to send and receive messages from every other node in the system. This can be particularly problematic in large systems with many nodes, as it may result in many messages being transmitted and processed.
- **May have high latency**: This solution may also have high latency, as it requires all nodes to wait for the total order to be determined before delivering their messages. This can be particularly problematic in systems where low latency is critical.

### Properties of Sockets

Sockets are a programming interface that enables communication between networked computers. They are used to send and receive data over a network connection using either TCP (Transmission Control Protocol) or UDP (User Datagram Protocol) connections.

Socket properties include:

- **Using either TCP or UDP connections**: Sockets can use either TCP or UDP connections to communicate with other computers over a network. TCP provides a reliable, connection-oriented communication channel, while UDP provides a connectionless, unreliable communication channel.
- **Serving as a programming interface**: Sockets provide a programming interface that enables applications to send and receive data over a network connection. They are typically used in conjunction with other programming constructs, such as threads or event loops, to enable concurrent communication and data processing.
- **A specification of "Host", "Port", "Connection type"**: Sockets are identified by a combination of a host, port, and connection type. The host specifies the address of the computer on which the socket is running, the port specifies a specific communication endpoint on the host, and the connection type specifies whether the socket is using TCP or UDP.
- **A unique address of a channel endpoint**: Each socket is assigned a unique address that identifies it as a communication endpoint. This address is used to identify the socket when sending or receiving data over the network.

### Berkeley Sockets

Berkeley sockets provide a set of primitives or functions that can be used to create, manage, and manipulate network connections and communication channels.

Here is a brief description of the meaning of each of the Berkeley Sockets primitives:

- **Socket**: The socket primitive creates a new communication endpoint, or socket, that can be used to send and receive data over a network connection.
- **Bind**: The bind primitive attaches a local address to a socket, specifying the address and port on which the socket will listen for incoming connections or data.
- **Listen**: The listen primitive announces the willingness of a socket to accept incoming connections from other hosts.
- **Accept**: The accept primitive blocks the caller until a connection request arrives at the socket. When a connection request is received, it creates a new socket for the connection and returns a reference to the new socket.
- **Connect**: The connect primitive actively attempts to establish a connection to a remote host by sending a connection request to the remote host.
- **Send**: The send primitive sends some data over the connection associated with a socket.
- **Receive**: The receive primitive receives some data over the connection associated with a socket.
- **Close**: The close primitive releases the connection associated with a socket, allowing it to be used for other purposes.

### Server Side Processing using Processes

Server-side processing using processes is a model for handling incoming requests in a networked system. It involves the following steps:

1. Server: The server listens on a specified port, waiting for incoming connection requests.
2. Client: A client connects to the server on an arbitrary port and establishes a connection between the client and the server.
3. Server: The server accepts the connection request and spawns a new process to handle the request. The process is assigned to the same port as the original connection, and the server goes back to listening for new connection requests.

This model allows the server to scale to some degree, as it can handle multiple requests concurrently by spawning new processes to handle each request. However, process creation can be expensive, and there may be limits on the number of processes that can be created on a given system. An example of this model is traditional CGI processing in a web server, where a new process is spawned to handle each incoming request.

### Server Side Processing using Threads

Server-side processing using threads is a model for handling incoming requests in a networked system that is similar to the process-based model, but uses threads instead of processes to handle requests. It involves the following steps:

1. Server: The server listens on a specified port, waiting for incoming connection requests.
2. Client: A client connects to the server on an arbitrary port and establishes a connection between the client and the server.
3. Server: The server accepts the connection request and spawns a new thread to handle the request. The thread is assigned to the same port as the original connection, and the server goes back to listening for new connection requests.

This model allows the server to scale well, as it can handle multiple requests concurrently by spawning new threads to handle each request. Thread creation is less expensive than process creation, and it is possible to create a larger number of threads on a given system. An example of this model is servlet request processing in a servlet engine, also known as a "web container".

In a threaded server, it is important to ensure that the functions that are used to handle incoming requests are re-entrant, or able to be safely called concurrently by multiple threads. This is because multiple threads may be executing the same function simultaneously, and the function must be able to handle this without causing problems.

To ensure that functions are re-entrant, it is important to avoid using unprotected global variables, as these can be modified concurrently by multiple threads, leading to potential race conditions and other problems. Instead, state should be kept on the stack, with each thread having its own copy of the state. This ensures that each thread has its own private version of the state, and can operate independently of other threads.

### Design Considerations for Socket-Based Services

- **Message formats**: The message formats that will be exchanged between clients and servers should be carefully designed to ensure that data can be transmitted and received correctly. This includes ensuring that data is represented consistently on different hardware platforms and avoiding problems caused by different data representations.
- **Protocol design**: The protocol that will be used by clients and servers to communicate should also be carefully designed. This includes deciding whether clients will wait for answers from the server (synchronous communication) or whether communication will be asynchronous, whether the server can call back to the client, whether the connection will be permanent or closed after each request, whether the server will hold client-related state (e.g. a session), and whether the server will allow concurrent requests.

### Stateless vs. Stateful Socket-Based Services

A stateless service is one in which the server does not store any information about previous requests or maintain any state between requests. This can have several advantages, including:

- **Scaling extremely well**: Because the server does not maintain any state between requests, it can handle a large number of requests concurrently without running out of resources or becoming overloaded.
- **Making denial of service attacks harder**: Because the server does not maintain any state between requests, it is more resistant to denial of service attacks, as attackers cannot exhaust resources by sending a large number of requests that require the server to store state.
- **Forcing new authentication and authorization per request**: A stateless service can require clients to authenticate and authorize each request separately, improving security by requiring clients to prove their identity and permissions for each request; this can however also be a disadvantage, as it requires a significant overhead to transfer the authn credentials each time.

On the other hand, a stateful service is one in which the server stores information about previous requests and maintains state between requests. This can have several advantages, including:

- **Allowing transactions and delivery guarantees**: Because the server maintains state between requests, it is possible to use transactions and guarantee delivery of requests.
- **Enabling more complex interactions**: A stateful service can support more complex interactions between clients and servers, as it allows the server to track the state of the interaction and respond appropriately.

However, stateful services can also have some drawbacks, including:

- **Risk of resource exhaustion**: Because the server maintains state between requests, it is possible for the server to run out of resources, such as sockets, if it receives many requests that require it to store state.
- **Need for reliable hardware and networks**: In order to function correctly, stateful services typically require reliable hardware and networks, as they rely on the server being able to maintain state between requests. If the server or network experiences failures, this can disrupt the stateful interaction.

### TCP SYN Flooding

TCP SYN flooding is a type of denial of service (DoS) attack that exploits a weakness in the TCP connection establishment process. In a normal TCP connection, the client sends a SYN (synchronize) packet to the server to initiate the connection, and the server responds with a SYN-ACK (synchronize-acknowledge) packet to confirm that the connection can be established. The client then **sends an ACK** (acknowledge) packet to complete the three-way handshake and establish the connection.

In a TCP SYN flooding attack, the attacker sends a large number of SYN packets to the server, either from a single machine or from a network of compromised machines. The server responds to each SYN packet with a SYN-ACK packet, **but the client never completes the three-way handshake** by sending an ACK packet. As a result, the server is left waiting for the ACK packet, and the resources used to track the half-open connections can be exhausted, preventing the server from accepting any new connections.

TCP SYN flooding attacks can be **mitigated by implementing SYN cookies**, which use cryptographic techniques to allow the server to track half-open connections without using any resources. Other measures, such as rate limiting and filtering of incoming SYN packets, can also help to prevent or mitigate the effects of TCP SYN flooding attacks.

### Writing a Socket Client & Server

For the server:

1. **Define the port number of the service**: The server should specify the port number on which it will listen for incoming connections. For example, the HTTP server typically listens on port 80.
2. **Allocate a server socket**: The server creates a server socket and binds it to the specified port number. The server socket then listens for new connections.
3. **Accept an incoming connection**: When a client attempts to connect to the server, the server socket accepts the connection and creates a new socket for the client connection.
4. **Get the input channel**: The server reads the input channel from the socket to receive messages from the client.
5. **Parse the client message**: The server parses the client message to understand the request being made.
6. **Get the output channel**: The server gets the output channel from the socket, which is where it will send responses to the client.
7. **Do request processing**: The server processes the client request, either by handling it directly or by creating a new thread to handle it.
8. **Create a response message**: The server creates a response message, such as an HTTP response, to send back to the client.
9. **Write the message to the output channel**: The server writes the response message to the output channel, which sends it back to the client.
10. **Read new messages or close the connection**: The server can either read new messages from the client's input channel or close the connection if it is no longer needed.

**For the client**:

1. **Define the hostname and port number** of the server host
2. **Allocate a socket** with the host and port parameters
3. **Obtain the input channel** (for messages from the server) and output channel (for messages to the server) from the socket
4. **Create a message** to send to the server, such as "GET /somefile.html HTTP/1.0"
5. **Write the message** to the output channel to send it to the server
6. **Read the response** from the input channel and display it

**For a multithreaded client:**

- One thread reads from the console and writes to the output channel
- The other thread reads from the input channel and displays or writes the server messages

### Distribution Transparency with Sockets

- **Invocation**: Server-side functions cannot be called directly from the client side, and messages must be defined and sent using socket operations
- **Location/relocation/migration**: If the service moves, the client connection will be broken
- **Replication/concurrency**: Not supported
- **Failure**: Not supported
- **Persistence**: Not supported

### Infrastructure of Client-Server Systems

1. **Directory**: Helps locate the server
2. **Proxy**: Checks client authorization and routes requests through the firewall
3. **Firewall**: Allows outgoing calls only
4. **Reverse proxy**: Caches results, ends SSL sessions, and authenticates clients
5. **Authentication server**: Stores client data and authorizes clients
6. **Load balancer**: Distributes requests across servers

## Remote Procedure Calls

### Overview

1. Call versions: local, inter-process, and remote
2. Mechanics of remote calls:
   1. Marshaling/serialization
   2. Data representation
   3. Message structure and schema evolution
   4. Interface definition language
   5. Tooling: generators
3. Cross-language call infrastructures: Thrift and gRPC

### Call Versions

1. **Local calls**: made within a single process and do not require network communication
2. **Inter-process calls**: Made between processes on the same machine and can be implemented using a variety of mechanisms, such as shared memory or pipes
3. **Remote calls**: Made between processes on different machines and typically require network communication

### Remote Calls vs. Remote Messages

- **Remote calls**: Hide the remote service calls behind a programming language call and are tightly coupled with synchronous processing
- **Remote messages**: Use a message-based middleware and create a new concept of a message and its delivery semantics; a message system can simulate a call-based system, but not vice versa

### In-Process (Local) Calls

- **No special middleware is required** for calls made within the same programming language
- Calls into the OS are not inter-process calls
- Special attention is required for cross-language calls made within a single process, such as calls to native code in Java
- In-process calls **are fast** because they do not require network communication or context switches between processes.
- Have **"exactly once"** semantics, meaning that they will be executed only once and will not be retried if they fail.
- Are **type-safe and link-safe**, meaning that they are checked for type compatibility at compile time and will not result in linker errors. However, they may have issues with dynamic loading if the called code is not available at runtime.
- Can be **either sequential or concurrent**, depending on the design of the application. Concurrent in-process calls can be implemented using threads or other concurrency mechanisms.
- Operate **within a single name and address space**, which means that they can access all variables and functions within the process without requiring additional addressing or mapping.
- Are **independent of byte ordering**, which means that they can be used on any machine with any endianness without requiring additional conversions.
- Can be **controlled in their memory usage**, such as through garbage collection, which can help prevent memory leaks and improve the performance and stability of the application.
- Can use **value or reference parameters**, depending on the needs of the application. Value parameters are copied when passed to a function, while reference parameters are passed by address and can be modified within the called function.
- Are **transparent programming language calls** and not explicit messages, which means that they appear to the programmer as regular function calls and do not require the creation and handling of explicit messages.

### Inter-Process Calls (IPC)

- Local inter-process calls are faster than remote calls, but **not as fast as in-process calls**
- Do **not have "exactly once"** semantics
- Are **type-safe and link-safe** if both processes use the same static libraries, but may have issues with dynamic loading
- Can be **either sequential or concurrent**, but the caller no longer controls the execution; the receiver must protect itself from concurrent access
- **Cannot assume a single name and address space** and require additional addressing or mapping
- Are still **independent of byte ordering**
- **Require cross-process garbage collection** to manage memory usage
- **Can only use value parameters**, as the target process cannot access memory in the calling process
- Are **not real programming language "calls"** and require the creation of messages to simulate the missing features
- Inter-process communication is not local and introduces **latency, memory barriers, and the possibility of process failures**

The good news is that inter-process communication occurs on the same hardware and uses the same language at the sender and receiver, which **can reduce security issues** and ensure that a system crash affects both sender and receiver (fail-stop semantics)

### Remote Procedure Calls (RPC)

- Remote procedure calls (RPCs) are **much slower than local calls** and **do not have delivery guarantees** without a protocol
- May have **version mismatches** that show up at runtime
- Are **concurrent** and the caller no longer controls the execution; the callee must protect itself from concurrent access
- **Cannot assume a single name and address space** and require additional addressing or mapping
- Are **affected by byte ordering**
- May **require network garbage collection** if they are stateful
- May **involve cross-language calls**
- **Can only use value parameters**, as the target process cannot access memory in the calling process
- **Are not real programming language "calls"** and require the creation of messages to simulate the missing features
- Often stateless

### Mechanics of Remote Calls

- **Marshaling/Serialization**: Process of converting program data into a format that can be transmitted over a network
- **External Data-Representation**: Standardized format for representing binary data
- **Interface Definition**: Defines a service, a set of related functions that can be accessed remotely
- **Message Structure and Evolution**: Way in which data is organized and transmitted between systems
- **Compilers**: Generate code (stub/skeleton or proxy) to facilitate communication between systems
- **Request/Reply Protocol**: Handles errors that may occur during the remote call process
- **Process/I/O Layer**: Responsible for managing threads and input/output operations

### Marshaling/Serialization

Marshaling/serialization is the process of converting parameters (basic types or objects) into a common transfer format (message) that can be transmitted over a network. At the target site, the message is transformed back into the original types or objects. There are several different approaches to marshaling/serialization, each with its own trade-offs:

- **Language-dependent output format**: This approach uses a proprietary format that is specific to a particular programming language. It may be slower and have limitations in expressiveness, but it can be more efficient in terms of the size of the message.
- **Language-independent output format**: This approach uses a standardized format that is not tied to any particular programming language. It may be more verbose and result in larger messages, but it is more flexible and can be used with a wider range of languages.
- **Binary schema-based**: In this approach, the sender and receiver both have a shared understanding of the structure of the message, including the types and variables contained within it. Function names are replaced with numbers and variable data is encoded to save space. This approach is efficient in terms of message size, but it can be inflexible.
- **Binary self-describing**: In this approach, the message contains information about its own structure, including the types and variables contained within it. This allows for more flexibility, but it requires the involved languages to have some level of flexibility in their capabilities.
- **Textual, self-describing**: This approach uses an XML representation of the types or objects contained in the message. It is flexible, but it can be verbose and result in larger messages.
- **Textual with schema for reader/writer**: This approach uses a schema to define the structure of the message, which allows for advanced schema evolution and dynamic serializations. It can be flexible, but it may result in larger messages.

**Serialization to text** is a method of converting data into a human-readable format, typically using a markup language such as XML. This approach can be less efficient in terms of the size of the resulting message, as it is generally less compact than binary serialization. It is important to be aware of language limits, such as the range of integers and floating-point numbers that can be represented in JavaScript, when using this approach. XML is a popular choice for language-independent encoding because it is widely supported and can represent a wide range of data types.

**Serialization to binary** is a method of converting data into a compact, machine-readable format. It requires a schema, which defines the structure of the message and the types of data it contains. This approach is generally more efficient in terms of the size of the resulting message, but it is not as flexible as text-based serialization because it requires a shared understanding of the schema between the sender and receiver. Binary serialization can also be used for language-independent encoding.

### Schema Evolution

When data or functions change, it is important to consider how different versions of a system will coexist and communicate with each other.

**Forward compatibility** means that older receivers should be able to understand messages from newer senders. This allows newer versions of a system to be deployed without causing problems for existing clients.

**Backward compatibility** means that newer receivers should be able to understand messages from older senders. This allows older versions of a system to continue functioning even after newer versions have been introduced.

### Keeping Compatibility when Evolving a Schema

> For JSON

**Forward compatibility** means that older versions of a system should be able to understand messages from newer versions. Examples of changes that can be made to a system in a way that maintains forward compatibility:

- **Adding a new required field**: Older readers will simply ignore the new field, so they will be compatible with newer versions.
- **Narrowing a numerical type (e.g. float to int)**: Older readers will assume ints, which are a subset of floats, so they will be compatible with the newer int type.

**Backward compatibility** means that newer versions of a system should be able to understand messages from older versions. Examples of changes that can be made to a system in a way that maintains backward compatibility:

- **Adding a field with a default value**: Older writers will be unaware of the new field, so they will use the default value instead.
- **Adding an optional field**: Older writers will be unaware of the new field, so they will use the default value (usually null) instead.
- **Widening a numerical type** (e.g. int to float): Older writers will always use ints, which are a subset of floats, so they will be compatible with the newer float type.
- **Removing a field**: Newer readers will ignore whatever was previously written in the field that was removed, so they will be compatible with older versions.

**Full compatibility** means that a change can be made to a system without breaking compatibility with either older or newer versions. Examples of changes that can be made to a system in a way that maintains full compatibility include:

- **Adding a field** with a default value
- **Adding an optional field**

**Incompatibility** means that a change to a system will break compatibility with either older or newer versions. Examples of changes that can break compatibility include:

- **Renaming** a field
- **Changing the type** of a field (other than the numeric conversions mentioned above)

### Stubs and Skeletons

Stubs and skeletons are code that is used to facilitate communication between different systems, typically in the context of remote procedure calls (RPCs). Stubs are used by clients to initiate a remote call, while skeletons are used by servers to receive and process the remote call.

There are several ways to generate stubs and skeletons, including:

- - **Generating them in advance from an interface definition language (IDL) file**: In this approach, the stubs and skeletons are generated from an IDL file, which defines the interfaces and data structures that are used for communication. The IDL file is used as a blueprint for generating the code.
- **Generating them on demand from a class file**: In this approach, the stubs and skeletons are generated from a class file, which defines the classes and methods that are used for communication. The class file is used as a blueprint for generating the code.
- **Distributing them in advance** to all clients and servers: In this approach, the stubs and skeletons are generated in advance and distributed to all the clients and servers that will be using them. This allows the systems to be set up and configured in advance, rather than on demand.
- **Downloading them on demand**: In this approach, the stubs and skeletons are downloaded by the clients and servers as needed, rather than being distributed in advance. This allows for more flexibility and can be more efficient in terms of bandwidth usage.

### Finding an RPC Server

In a remote procedure call (RPC) system, a client needs to be able to locate the server in order to initiate a remote call.

**Service:**

1. **Start listening at port X**: The server starts listening for incoming requests on a specific port.
2. **Tell portmapper about program, version, and port**: The server registers itself with the portmapper, which is a service that keeps track of the programs and ports that are available on the system. The portmapper is typically a separate daemon that runs on the system.

**Client:**

1. **Ask portmapper for program, version**: The client sends a request to the portmapper asking for the port number of the desired program and version.
2. The **portmapper responds** with the port number where the desired program and version can be found.
3. **Send procedure call** to service: The client sends the procedure call to the server on the specified port.

This process is known as "binding," and there are several ways to handle it, including using inetd, DCE, or a Unix portmapper.

### Factors to Consider when Choosing an IDL

- **Are data types easily expressed using the IDL?** It is important to choose an IDL that can easily represent the types of data that will be used in the RPC system.
- **Is hard or soft versioning used?** Hard versioning means that the IDL is strictly enforced, and any changes to the IDL will break compatibility. Soft versioning means that the IDL is more flexible and can be changed without breaking compatibility.
- **Are structures self-describing?** Self-describing structures contain enough information to be understood by any system, even if it is not familiar with the specific structure. This can be useful for maintaining compatibility between different versions of a system.
- **Is it possible to change the structures later and keep backward compatibility?** It is important to choose an IDL that allows for changes to be made to the structures in a way that maintains backward compatibility with older versions of the system.
- **Is it possible to change processing of structures later and keep forward compatibility?** It is important to choose an IDL that allows for changes to be made to the processing of structures in a way that maintains forward compatibility with newer versions of the system.
- **Are there bindings for all languages in use at my company?** It is important to choose an IDL that has bindings for all the languages that will be used in the RPC system.
- **Do I need different encodings (binary/textual)?** It is important to consider whether binary or textual encoding will be needed for the RPC system, and choose an IDL that supports the desired encoding.
- **Does changing serialization require a recompile?** It is important to consider whether changes to the serialization will require a recompile, as this can affect the flexibility and ease of maintenance of the system.
- **Can I extend/change the runtime system (e.g. add trace statements)?** It is important to choose an IDL that allows for changes and extensions to the runtime system, such as the ability to add trace statements.

### Popular IDLs for RPCs

- **CORBA (Common Object Request Broker Architecture)**: CORBA is a standard for interoperating between different programming languages and platforms. It defines an interface definition language (IDL) that can be used to describe the interfaces and data structures that are used for communication, as well as a runtime system for executing the RPCs.
- **Microsoft CLR (Common Language Runtime)**: The CLR is a runtime environment for executing .NET programs. It includes a cross-language call infrastructure that allows programs written in different .NET languages to communicate with each other.
- **Thrift**: Thrift is a cross-platform RPC framework that allows different programming languages to communicate with each other. It includes an IDL for defining the interfaces and data structures that are used for communication, as well as code generators for generating the stubs and skeletons that are used to initiate and process the RPCs.
- **gRPC**: gRPC is a high-performance RPC framework that uses HTTP/2 as the underlying transport. It includes an IDL for defining the interfaces and data structures that are used for communication, as well as code generators for generating the stubs and skeletons that are used to initiate and process the RPCs.
