# RabbitMQ

## Overview

RabbitMQ is a robust, feature-rich message broker that implements the Advanced Message Queuing Protocol (AMQP). It's designed to handle complex routing scenarios, reliable message delivery, and enterprise-grade messaging requirements with support for multiple messaging patterns.

## Data Model

### Core Concepts

```mermaid
graph TB
    subgraph "RabbitMQ Broker"
        subgraph "Exchange Types"
            DIRECT[Direct Exchange]
            TOPIC[Topic Exchange]
            FANOUT[Fanout Exchange]
            HEADERS[Headers Exchange]
        end
        
        subgraph "Queues"
            Q1[Queue 1]
            Q2[Queue 2]
            Q3[Queue 3]
            DLQ[Dead Letter Queue]
        end
        
        subgraph "Routing"
            RK[Routing Keys]
            BIND[Bindings]
            FILTER[Message Filters]
        end
    end
    
    subgraph "Publishers"
        P1[Publisher 1]
        P2[Publisher 2]
    end
    
    subgraph "Consumers"
        C1[Consumer 1]
        C2[Consumer 2]
        C3[Consumer 3]
    end
    
    P1 --> DIRECT
    P1 --> TOPIC
    P2 --> FANOUT
    P2 --> HEADERS
    
    DIRECT --> Q1
    TOPIC --> Q2
    FANOUT --> Q1
    FANOUT --> Q2
    FANOUT --> Q3
    HEADERS --> Q3
    
    Q1 --> C1
    Q2 --> C2
    Q3 --> C3
    
    Q1 --> DLQ
    Q2 --> DLQ
    Q3 --> DLQ
    
    RK --> BIND
    BIND --> FILTER
    FILTER --> DIRECT
    FILTER --> TOPIC
```

### Data Structure Components

#### Exchanges
- **Direct Exchange**: Routes messages with exact routing key match
- **Topic Exchange**: Routes messages with pattern matching using wildcards (* and #)
- **Fanout Exchange**: Broadcasts messages to all bound queues (ignores routing key)
- **Headers Exchange**: Routes based on message headers instead of routing keys

#### Queues
- **Standard Queues**: FIFO message storage with persistence options
- **Priority Queues**: Messages with higher priority are consumed first
- **Dead Letter Queues**: Store messages that cannot be processed
- **Lazy Queues**: Move messages to disk as early as possible to reduce memory usage

#### Routing Components
- **Routing Keys**: String values used to route messages to specific queues
- **Bindings**: Link between an exchange and a queue with routing criteria
- **Message Filters**: Additional criteria for message routing based on headers or properties

### Message Format

```json
{
  "properties": {
    "message_id": "msg-12345",
    "correlation_id": "req-67890",
    "reply_to": "response-queue",
    "delivery_mode": 2,
    "priority": 5,
    "timestamp": 1641916455000,
    "type": "order.created",
    "content_type": "application/json",
    "content_encoding": "utf-8",
    "headers": {
      "source": "order-service",
      "version": "1.0"
    }
  },
  "body": {
    "orderId": "order-123",
    "customerId": "cust-456",
    "items": [
      {
        "productId": "prod-789",
        "quantity": 2
      }
    ]
  }
}
```

## Architecture Overview

### Single Node Architecture

```mermaid
graph TB
    subgraph "RabbitMQ Node"
        BEAM[Erlang VM]
        
        subgraph "Core Components"
            CONN[Connection Manager]
            CHAN[Channel Manager]
            EXCH[Exchange Manager]
            QUEUE[Queue Manager]
            ROUTE[Router]
        end
        
        subgraph "Storage"
            DISK[Disk Storage]
            MEM[Memory Storage]
        end
        
        subgraph "Management"
            MGMT[Management Plugin]
            STATS[Statistics]
        end
    end
    
    subgraph "Clients"
        PUB[Publishers]
        SUB[Consumers]
        ADMIN[Admin Tools]
    end
    
    PUB --> CONN
    SUB --> CONN
    ADMIN --> MGMT
    
    CONN --> CHAN
    CHAN --> EXCH
    EXCH --> ROUTE
    ROUTE --> QUEUE
    
    QUEUE --> DISK
    QUEUE --> MEM
    
    MGMT --> STATS
```

### Clustered Architecture

```mermaid
graph TB
    subgraph "RabbitMQ Cluster"
        subgraph "Node 1 (Disk)"
            N1[RabbitMQ Node 1]
            D1[Disk Storage]
        end
        
        subgraph "Node 2 (RAM)"
            N2[RabbitMQ Node 2]
            D2[RAM Storage]
        end
        
        subgraph "Node 3 (Disk)"
            N3[RabbitMQ Node 3]
            D3[Disk Storage]
        end
        
        subgraph "Load Balancer"
            LB[HAProxy/Nginx]
        end
    end
    
    subgraph "External Systems"
        APP[Applications]
        MONITOR[Monitoring]
    end
    
    APP --> LB
    LB --> N1
    LB --> N2
    LB --> N3
    
    N1 -.-> N2
    N2 -.-> N3
    N3 -.-> N1
    
    N1 --> D1
    N2 --> D2
    N3 --> D3
    
    N1 --> MONITOR
    N2 --> MONITOR
    N3 --> MONITOR
```

## Target Operating Model (TOM)

### Without High Availability

#### Single Node Setup

| Component | Specification | Purpose |
|-----------|---------------|---------|
| **RabbitMQ Node** | 1 instance | Message broker |
| **Erlang VM** | Single process | Runtime environment |
| **Storage** | Local disk | Message persistence |
| **Management** | Web UI enabled | Administration |

#### Resource Requirements

| Resource | Minimum | Recommended | Purpose |
|----------|---------|-------------|---------|
| **CPU** | 2 cores | 4+ cores | Message processing |
| **Memory** | 2GB | 4GB+ | Message buffering |
| **Storage** | 50GB | 200GB+ | Message persistence |
| **Network** | 100Mbps | 1Gbps+ | Client communication |

#### Configuration Example

```erlang
%% Single node configuration
[
  {rabbit, [
    {tcp_listeners, [5672]},
    {ssl_listeners, [5671]},
    {disk_free_limit, {mem_relative, 1.0}},
    {vm_memory_high_watermark, 0.4},
    {heartbeat, 60},
    {cluster_nodes, {[], disc}},
    {cluster_name, <<"rabbit@localhost">>}
  ]},
  {rabbitmq_management, [
    {listener, [{port, 15672}]}
  ]}
].
```

### With High Availability

#### Cluster Setup

| Component | Specification | Purpose |
|-----------|---------------|---------|
| **RabbitMQ Nodes** | 3+ instances | Fault tolerance |
| **Load Balancer** | HAProxy/Nginx | Traffic distribution |
| **Shared Storage** | Optional | Persistent data |
| **Monitoring** | Prometheus/Grafana | Cluster health |

#### Resource Requirements (Per Node)

| Resource | Minimum | Recommended | Purpose |
|----------|---------|-------------|---------|
| **CPU** | 4 cores | 8+ cores | Concurrent processing |
| **Memory** | 4GB | 8GB+ | Cluster coordination |
| **Storage** | 100GB | 500GB+ | Message persistence |
| **Network** | 1Gbps | 10Gbps+ | Inter-node communication |

#### Deployment Architecture

```mermaid
graph TB
    subgraph "Production Environment"
        subgraph "Availability Zone 1"
            N1[Node 1 - Disk]
            LB1[Load Balancer 1]
        end
        
        subgraph "Availability Zone 2"
            N2[Node 2 - RAM]
            LB2[Load Balancer 2]
        end
        
        subgraph "Availability Zone 3"
            N3[Node 3 - Disk]
            LB3[Load Balancer 3]
        end
        
        subgraph "Monitoring Stack"
            PROM[Prometheus]
            GRAF[Grafana]
            ALERT[AlertManager]
        end
        
        subgraph "Management"
            MGMT[RabbitMQ Management]
            SHOVEL[Shovel Plugin]
            FEDERATION[Federation Plugin]
        end
    end
    
    subgraph "Applications"
        PROD[Producers]
        CONS[Consumers]
        ADMIN[Admin Tools]
    end
    
    PROD --> LB1
    PROD --> LB2
    PROD --> LB3
    
    CONS --> LB1
    CONS --> LB2
    CONS --> LB3
    
    LB1 --> N1
    LB2 --> N2
    LB3 --> N3
    
    N1 -.-> N2
    N2 -.-> N3
    N3 -.-> N1
    
    N1 --> PROM
    N2 --> PROM
    N3 --> PROM
    
    PROM --> GRAF
    PROM --> ALERT
    
    ADMIN --> MGMT
```

#### HA Configuration

```erlang
%% High availability cluster configuration
[
  {rabbit, [
    {tcp_listeners, [5672]},
    {ssl_listeners, [5671]},
    {disk_free_limit, {mem_relative, 1.0}},
    {vm_memory_high_watermark, 0.4},
    {heartbeat, 60},
    {cluster_nodes, {['rabbit@node1', 'rabbit@node2', 'rabbit@node3'], disc}},
    {cluster_name, <<"production-cluster">>},
    {ha_policy, [
      {pattern, ".*"},
      {definition, [
        {ha_mode, exactly},
        {ha_params, 2},
        {ha_sync_mode, automatic}
      ]}
    ]}
  ]},
  {rabbitmq_management, [
    {listener, [{port, 15672}]}
  ]},
  {rabbitmq_shovel, []},
  {rabbitmq_federation, []}
].
```

## Pros and Cons

### Pros

#### Flexibility & Features
- **Rich Routing**: Complex routing with exchanges and bindings
- **Multiple Protocols**: AMQP, STOMP, MQTT, HTTP support
- **Message Patterns**: Request-reply, pub/sub, routing, topics
- **Plugin System**: Extensible with community plugins

#### Reliability & Durability
- **Message Persistence**: Durable queues and messages
- **Acknowledgments**: Flexible acknowledgment modes
- **Clustering**: Built-in clustering support
- **High Availability**: Queue mirroring and federation

#### Enterprise Features
- **Security**: SSL, SASL, LDAP integration
- **Management**: Web-based management interface
- **Monitoring**: Built-in metrics and monitoring
- **Priority Queues**: Message priority support

#### Developer Experience
- **Client Libraries**: Libraries for most programming languages
- **Documentation**: Comprehensive documentation
- **Community**: Active community and support
- **Standards Compliance**: AMQP 0-9-1 compliant

### Cons

#### Performance Limitations
- **Throughput**: Lower throughput compared to Kafka
- **Latency**: Higher latency for high-volume scenarios
- **Memory Usage**: Can be memory-intensive
- **Scaling**: Vertical scaling limitations

#### Operational Complexity
- **Erlang Dependency**: Requires Erlang/OTP knowledge
- **Configuration**: Complex configuration options
- **Clustering**: Cluster management complexity
- **Monitoring**: Requires specialized monitoring setup

#### Resource Requirements
- **Memory Intensive**: High memory usage for large queues
- **CPU Overhead**: Significant CPU for message routing
- **Storage**: Persistent storage requirements
- **Network**: Cluster communication overhead

#### Use Case Constraints
- **High Volume**: Not ideal for very high-volume scenarios
- **Stream Processing**: Limited stream processing capabilities
- **Long-term Storage**: Not designed for long-term message retention
- **Ordering**: No guaranteed message ordering

## Best Practices

### Production Deployment

1. **Cluster Configuration**
   - Use odd number of nodes (3 or 5)
   - Mix of disk and RAM nodes
   - Proper network configuration

2. **Queue Design**
   - Use appropriate queue types (classic vs quorum)
   - Set proper TTL and dead letter exchanges
   - Implement queue mirroring for HA

3. **Monitoring**
   - Monitor queue depths and consumer rates
   - Set up alerts for memory and disk usage
   - Use RabbitMQ management plugin

4. **Security**
   - Enable SSL/TLS encryption
   - Use proper authentication and authorization
   - Implement network security

### Development Guidelines

1. **Connection Management**
   - Use connection pooling
   - Handle connection failures gracefully
   - Implement proper cleanup

2. **Message Design**
   - Use appropriate message persistence
   - Implement proper error handling
   - Design for idempotency

3. **Performance Optimization**
   - Batch message publishing
   - Use appropriate prefetch settings
   - Monitor and tune queue performance

## When to Choose RabbitMQ

### Ideal Use Cases
- **Complex Routing**: Multi-step message routing
- **Enterprise Integration**: Legacy system integration
- **Task Queues**: Background job processing
- **Request-Reply**: Synchronous communication patterns
- **Microservices**: Service-to-service messaging

### Consider Alternatives When
- **High Volume**: Millions of messages per second
- **Stream Processing**: Real-time analytics
- **Long-term Storage**: Event sourcing requirements
- **Simple Pub/Sub**: Basic publish-subscribe patterns
- **Resource Constraints**: Limited memory/CPU resources
