# Glossary

## A

**Acknowledgment (ACK)**
: A signal sent by a message consumer to indicate that a message has been successfully processed.

**Apache Kafka**
: A distributed streaming platform designed for building real-time data pipelines and streaming applications.

**Apache Pulsar**
: A multi-tenant, high-performance solution for server-to-server messaging with features like multi-tenancy, geo-replication, and tiered storage.

**Asynchronous Messaging**
: A communication pattern where the sender doesn't wait for a response from the receiver before continuing.

**At-least-once Delivery**
: A message delivery guarantee where messages are delivered one or more times, but duplicates are possible.

**At-most-once Delivery**
: A message delivery guarantee where messages are delivered at most once, but message loss is possible.

## B

**Broker**
: A server that acts as an intermediary for message routing between producers and consumers.

**Backpressure**
: A mechanism to handle situations where message consumers cannot keep up with the rate of incoming messages.

## C

**Consumer**
: An application or component that receives and processes messages from a messaging system.

**Consumer Group**
: A group of consumers that work together to process messages from a topic or queue, typically for load balancing.

**Connection Pooling**
: A technique to reuse connections to reduce the overhead of establishing new connections for each message.

## D

**Dead Letter Queue (DLQ)**
: A queue where messages that cannot be processed successfully are sent for later analysis or manual intervention.

**Durable Subscription**
: A subscription that persists even when the subscriber is offline, ensuring message delivery when it reconnects.

## E

**Event Sourcing**
: A pattern where state changes are stored as a sequence of events, allowing the system to reconstruct state from these events.

**Exactly-once Delivery**
: A message delivery guarantee where each message is delivered exactly once, with no duplicates or losses.

**Exchange**
: In RabbitMQ, a component that receives messages from producers and routes them to queues based on routing rules.

## F

**Fanout**
: A messaging pattern where a single message is delivered to multiple consumers.

**FIFO (First In, First Out)**
: A queue processing order where messages are processed in the order they were received.

## H

**High Availability (HA)**
: The ability of a system to remain operational even when some components fail.

**Horizontal Scaling**
: Adding more servers or instances to handle increased load.

## I

**Idempotency**
: The property that allows an operation to be performed multiple times without changing the result beyond the initial application.

**In-memory Messaging**
: Messaging systems that store messages in memory for high-speed processing, typically sacrificing durability.

## J

**JMS (Java Message Service)**
: A Java API that allows applications to create, send, receive, and read messages in enterprise messaging systems.

## K

**Kafka Connector**
: A component that connects Kafka to external systems for data import/export.

**Kafka Streams**
: A client library for building applications that process and analyze data stored in Kafka.

## L

**Load Balancing**
: Distributing incoming messages across multiple consumers to improve performance and reliability.

**Log Compaction**
: A feature in Kafka that ensures only the latest value for each key is retained in a topic.

## M

**Message**
: A unit of data transmitted between applications or components in a messaging system.

**Message Broker**
: A software component that facilitates communication between different applications by translating messages between protocols.

**Message Queue**
: A form of asynchronous service-to-service communication used in serverless and microservices architectures.

**MQTT (Message Queuing Telemetry Transport)**
: A lightweight messaging protocol designed for IoT devices and low-bandwidth, high-latency networks.

## N

**NATS**
: A high-performance messaging system designed for cloud-native applications, IoT messaging, and microservices.

## O

**Offset**
: A unique identifier for a message within a partition, used to track message consumption progress.

**Ordering**
: The guarantee that messages are processed in a specific sequence.

## P

**Partition**
: A way to divide a topic into multiple segments to enable parallel processing and scalability.

**Persistent Message**
: A message that is stored on disk and survives broker restarts.

**Producer**
: An application or component that sends messages to a messaging system.

**Publish-Subscribe (Pub/Sub)**
: A messaging pattern where producers (publishers) send messages to topics, and consumers (subscribers) receive messages from topics they're interested in.

## Q

**Queue**
: A data structure that stores messages in a first-in-first-out (FIFO) manner.

**Quorum**
: The minimum number of nodes required to be available for the system to function properly.

## R

**RabbitMQ**
: An open-source message broker that implements the Advanced Message Queuing Protocol (AMQP).

**Replication**
: The process of copying data across multiple nodes to ensure fault tolerance and high availability.

**Routing Key**
: A message attribute used by the message broker to determine which queue(s) should receive the message.

## S

**Saga Pattern**
: A design pattern for managing distributed transactions across multiple services.

**Scaling**
: The ability to handle increased load by adding resources (vertical scaling) or more instances (horizontal scaling).

**Serialization**
: The process of converting data structures into a format suitable for transmission over a network.

**Service Bus**
: An enterprise messaging infrastructure that provides reliable message delivery between distributed applications.

**Solace**
: A messaging platform that provides event-driven communication for enterprise applications.

**Stream Processing**
: The processing of data in motion, analyzing and acting on data as it flows through the system.

## T

**Topic**
: A category or feed name to which messages are published in a pub/sub messaging system.

**Throughput**
: The number of messages that can be processed per unit of time.

**Transactional Messaging**
: A messaging pattern that ensures messages are processed as part of a transaction, maintaining ACID properties.

## V

**Vertical Scaling**
: Adding more power (CPU, RAM) to existing servers to handle increased load.

## W

**WebSocket**
: A communication protocol that provides full-duplex communication channels over a single TCP connection.

**WAN (Wide Area Network)**
: A network that spans large geographical areas, often requiring specialized messaging considerations.

## Z

**ZeroMQ**
: A high-performance asynchronous messaging library that provides message queuing without a message broker.

**Zookeeper**
: A coordination service used by distributed systems, notably used by Apache Kafka for cluster management.
