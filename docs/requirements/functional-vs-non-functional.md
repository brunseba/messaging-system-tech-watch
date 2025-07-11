# Functional vs Non-Functional Requirements

This section helps distinguish between functional and non-functional requirements to aid in the selection of an appropriate messaging system.

## Functional Requirements

Functional requirements describe the specific behaviors, features, and functions a messaging system must provide. Key aspects include:

- **Message Delivery**: Ensure messages are delivered from sender to recipient(s).
- **Supported Messaging Patterns**: Include support for Pub-Sub, Request-Reply, Fanout, Push-Pull, etc.
- **Integration**: Ability to connect with specified applications, APIs, or protocols (e.g., AMQP, MQTT).
- **Message Routing**: Support for routing rules and filtering.
- **Persistence**: Option to store messages for later retrieval.
- **Error Handling**: Mechanisms for failed message deliveries.
- **User Authentication**: Ensure only authorized users or systems can send/receive messages.
- **Monitoring and Logging**: Ability to track message flow and system events.
- **Administration Tools**: Interfaces for managing queues, topics, and users.

## Non-Functional Requirements

Non-functional requirements specify the quality attributes, performance, and constraints of the system:

- **Scalability**: Handle increasing loads without performance degradation.
- **Latency**: Deliver messages within a defined time frame.
- **Throughput**: Process a minimum number of messages per second.
- **Reliability**: Guarantees about message delivery.
- **Availability**: System uptime requirements.
- **Durability**: Assurance that messages are not lost in case of failures.
- **Security**: Encryption of messages in transit and at rest; access controls.
- **Maintainability**: Ease of updates and modifications.
- **Portability**: Ability to deploy on different platforms.
- **Compliance**: Adherence to industry standards or regulations.
- **Cost Constraints**: Budget for implementation and operation.
