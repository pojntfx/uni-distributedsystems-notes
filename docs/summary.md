---
author: [Felicitas Pojtinger]
date: "2022-12-17"
subject: "Uni Distributed Systems Summary"
keywords: [distributed-systems, hdm-stuttgart]
subtitle: "Summary for the distributed systems course at HdM Stuttgart"
lang: "en"
---

# Uni Distributed Systems Summary

## Summary Introduction

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
5. Remote objects and frameworks: This section covers the use of remote objects and frameworks, such as RMI and EJB, to enable communication between objects in a distributed system.
6. **Theoretical foundations of distributed systems**: This section covers key concepts and theories that are relevant to the design of distributed systems, including the FLP theorem, time, causality, consensus, eventual consistency, and optimistic replication.
7. **Distributed services and algorithms I**: This section covers the design and implementation of various distributed services and algorithms, including load balancing, message queues, caching, and consistent hashing.
8. **Distributed services II**: This section covers more advanced topics in distributed services, including persistence, transactions, eventual consistency, and coordination.
9. **Distributed security**: This section covers the key considerations for securing distributed systems, including authentication, authorization, and access control (AAA), secure delegation, and backend security.
10. **Design of distributed systems**: This section covers the methodology and principles for designing distributed systems, as well as examples of different architectures and design patterns.
11. **System management in distributed systems**: This section covers the key considerations for managing and maintaining distributed systems, including monitoring, chaos monkeys, and patterns of resilience.
12. **Service architectures**: This section covers different service architectures, including service-oriented architecture (SOA) and microservices.
13. **Peer-to-peer systems and the distributed web**: This section covers the use of peer-to-peer systems and technologies, such as distributed hashtables, blockchain, onion routing, and distributed consensus, in the context of the distributed web.
14. **Ultra-large-scale systems**: This section covers the design and implementation of ultra-large-scale systems, including considerations related to scalability, performance, network design, and datacenter design.

## 1. Introduction to Distributed Systems

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
- It provides glue code and generators that allow different programming languages and systems to interoperate.
- It controls messages and enforces delivery guarantees, such as at-least-once delivery.
- It reorders requests from participants to create a causal or total ordering.
- It takes over responsibility for messages and may store them temporarily.
- It creates groups of nodes that process events together and controls fail-over.
- It hides differences in hardware, location of services, and offers load balancing.
- It allows filtering of requests or provides means to add additional security information to calls.
- It provides powerful services such as locking, scheduling, and messaging to applications.
- It offers frameworks that provide automatic storage, security checks, and transactional control.
- It supports message bus architectures that provide loose coupling through publish/subscribe functions.

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
