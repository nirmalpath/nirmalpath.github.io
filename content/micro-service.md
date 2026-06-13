# Microservices Cheatsheet
## Mindmap

## Topics

- Intro
- 
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Intro
    Single Responsibility | Independent | Owns its data | Loosely Coupled | Cohesive | Tech Agnostic

### Typical Architecture
                      +------------------+
                      |   Client Apps    |
                      | Web / Mobile/API |
                      +--------+---------+
                               |
                               v
                      +------------------+
                      |   API Gateway    |
                      +--------+---------+
                               |
          +--------------------+-------------------+
          |                    |                   |
          v                    v                   v
    +---------------+   +---------------+   +---------------+
    | User Service  |   | Order Service |   | Product Svc   |
    +-------+-------+   +-------+-------+   +-------+-------+
            |                   |                   |
            v                   v                   v
     +------------+      +------------+      +------------+
     | User DB    |      | Order DB   |      | Product DB |
     +------------+      +------------+      +------------+

        <---- Event Bus / Message Broker ---->

### Core Components
    API Gateway (Entry point) --> Service Discovery --> Load Balancer --> Message Broker (Async comms) --> Config Server --> Database --> Monitoring --> Distributed Tracing

### Communication Patterns
    REST: client --> API GW --> Order Service
    gRPC (more complex): inventory service --> Product Service 
    Asyc: Order Created
              |
              v
            Kafka
              |
              +--> Inventory Service
              +--> Notification Service
              +--> Billing Service

### Database Pattern    
    Database per service | Shared (avoid)

### Service Discovert
    client-side: clietn --> registry --> service instance
    server-side: client --> load balancer --> service instance

### API GW Responsibilities
    Routing | Authentication (jwt, OAuth, SSO) | Rate Limiting | Caching 

### Data Consistency
    Saga pattern (distributed transactions): Types (Choreography, Orchestration)

### Resilience Patterns
    Circuit breker (prevents cascading failure) | Retry | Bulkhead (isolate failures) | Timeout

### Security
    Authentication: OAuth2, OpenID Connect, JWT | Authorization: RBAC, ABAC | Service to Service: mTLS, TLS, Certificates

### Observability
    Logging: Centralized | Metrics: CPU, Memory, Latency, Throughput, Error rate | Distributed tracing

### Event Streaming
    Kafka Arch: Producer
                 |
                 v
               Kafka Topic
                 |
                 +--> Consumer A
                 +--> Consumer B
                 +--> Consumer C

### Deployments
    Containers: Build --> Docker Image --> Deploy
    Kubernetes: Pod, Deployment, Service, Ingress, ConfigMap, Secret
    
