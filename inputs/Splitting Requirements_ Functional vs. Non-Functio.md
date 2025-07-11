# Splitting Requirements: Functional vs. Non-Functional

When evaluating or designing messaging systems, it's essential to distinguish between **functional** and **non-functional requirements**. This helps clarify what the system must do versus how well it must perform.

#### Functional Requirements

Functional requirements describe the **specific behaviors, features, and functions** a messaging system must provide. They answer the question: *What should the system do?*

- **Message Delivery:** The system must deliver messages from sender to recipient(s).
- **Supported Messaging Patterns:** Support for Pub-Sub, Request-Reply, Fanout, Push-Pull, etc.
- **Integration:** Ability to connect with specified applications, APIs, or protocols (e.g., AMQP, MQTT).
- **Message Routing:** Support for routing rules, filtering, and topic-based delivery.
- **Persistence:** Option to store messages for later retrieval or replay.
- **Error Handling:** Mechanisms for handling failed message deliveries or retries.
- **User Authentication:** Ensure only authorized users or systems can send/receive messages.
- **Monitoring and Logging:** Ability to track message flow, status, and system events.
- **Administration Tools:** Interfaces for managing queues, topics, and users.


#### Non-Functional Requirements

Non-functional requirements specify the **quality attributes, performance, and constraints** of the system. They answer: *How well should the system perform its functions?*

- **Scalability:** The system must handle increasing loads (more users, messages, or devices) without performance degradation.
- **Latency:** Messages should be delivered within a defined maximum time (e.g., sub-second delivery).
- **Throughput:** The system should process a minimum number of messages per second.
- **Reliability:** Guarantees about message delivery (e.g., at-least-once, exactly-once).
- **Availability:** System uptime requirements (e.g., 99.99% availability).
- **Durability:** Assurance that messages are not lost in case of failures.
- **Security:** Encryption of messages in transit and at rest; access controls.
- **Maintainability:** Ease of updates, bug fixes, and system modifications.
- **Portability:** Ability to deploy on different platforms (cloud, on-premises).
- **Compliance:** Adherence to industry standards or regulations (e.g., GDPR, HIPAA).
- **Cost Constraints:** Budgetary limits for implementation and operation.


#### Example Table

| Requirement Type | Examples |
| :-- | :-- |
| Functional | Message delivery, routing, integration, authentication, admin tools |
| Non-Functional | Scalability, latency, reliability, security, availability, compliance |

Clearly separating these requirements ensures a comprehensive evaluation and helps select or design a messaging system that fits both the business and technical needs.

