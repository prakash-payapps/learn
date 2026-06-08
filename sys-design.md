# System Design & Application Architecture — Learning Path

---

## 1. Fundamentals

- Client-Server Model
- OSI Model
- TCP/IP Model
- IP Addressing & Subnetting
- CIDR Notation
- DNS (Domain Name System)
- DNS Record Types (A, CNAME, MX, TXT, NS, SOA)
- HTTP / HTTPS
- HTTP/1.1 vs HTTP/2 vs HTTP/3
- QUIC Protocol
- Request / Response Cycle
- Stateless vs Stateful
- Ports & Sockets
- TCP vs UDP
- TCP Handshake (3-way, 4-way)
- Latency, Throughput, Bandwidth
- Availability, Reliability, Durability
- Availability in Parallel vs Series (composite availability)
- SLA / SLO / SLI
- Idempotency
- Caching Semantics
- Content Negotiation
- Timeouts
- Numbers Every Engineer Should Know (latency numbers)

---

## 2. Software Design Principles

- SOLID Principles (SRP, OCP, LSP, ISP, DIP)
- DRY (Don't Repeat Yourself)
- KISS (Keep It Simple, Stupid)
- YAGNI (You Aren't Gonna Need It)
- Separation of Concerns
- Composition over Inheritance
- Favour Immutability
- Law of Demeter
- Dependency Injection
- Inversion of Control (IoC)
- Encapsulation & Abstraction
- Coupling & Cohesion
- Fail Fast Principle
- 12-Factor App Methodology
- Design by Contract
- Defensive Programming
- Error Handling Strategies
- Configuration Design
- Architecture Decision Records

---

## 3. Object-Oriented & Functional Programming

- OOP Pillars (Encapsulation, Abstraction, Inheritance, Polymorphism)
- Classes, Interfaces, Abstract Classes
- Functional Programming Principles
- Pure Functions & Side Effects
- Immutability
- Higher-Order Functions
- First-Class Functions
- Referential Transparency
- Recursion vs Iteration
- Closures
- Lazy Evaluation
- Pattern Matching
- Type Systems

---

## 4. Design Patterns (GoF)

### Creational
- Singleton
- Factory Method
- Abstract Factory
- Builder
- Prototype

### Structural
- Adapter
- Bridge
- Composite
- Decorator
- Facade
- Flyweight
- Proxy

### Behavioral
- Chain of Responsibility
- Command
- Iterator
- Mediator
- Memento
- Observer
- State
- Strategy
- Template Method
- Visitor

---

## 5. Application Architecture Patterns

- MVC (Model-View-Controller)
- MVP (Model-View-Presenter)
- MVVM (Model-View-ViewModel)
- Layered (N-Tier) Architecture
- Hexagonal Architecture (Ports & Adapters)
- Clean Architecture
- Onion Architecture
- Pipe and Filter
- Repository Pattern
- Unit of Work Pattern
- Service Layer Pattern
- CQRS Pattern
- Specification Pattern
- Dependency Rule

---

## 6. APIs & Communication Protocols

- REST API (principles, constraints, best practices)
- HTTP Methods & Status Codes
- API Versioning
- GraphQL
- GraphQL Subscriptions
- gRPC
- WebSockets
- WebHooks
- Long Polling & Server-Sent Events (SSE)
- SOAP
- HATEOAS
- WebRTC
- MQTT
- AMQP
- SMTP / IMAP / POP3
- FTP / SFTP
- SSH
- WebTransport
- RSocket
- JSON-RPC

---

## 7. Data Formats & Serialisation

- JSON
- XML
- Protobuf
- Avro
- MessagePack
- Thrift
- CSV / Parquet / ORC (batch)
- YAML / TOML
- BSON
- CBOR
- HTML
- Markdown

---

## 8. Encoding, Hashing & ID Generation

- Base64 Encoding
- URL Encoding
- Hashing Algorithms (MD5, SHA-1, SHA-256)
- Password Hashing (bcrypt, scrypt, argon2)
- HMAC
- Checksums & Data Integrity
- UUID / GUID
- ULID
- Snowflake IDs
- Auto-increment vs Distributed ID Generation
- Surrogate vs Natural Keys
- Unicode & UTF-8
- Base58 Encoding
- KSUID
- NanoID

---

## 9. Security & Identity

- HTTPS / TLS / SSL
- TLS Handshake
- Certificates & PKI
- Certificate Transparency
- OAuth 2.0
- OAuth 2.0 Grant Types (Auth Code, PKCE, Client Credentials, Implicit)
- OpenID Connect (OIDC)
- JWT (JSON Web Tokens)
- JWT vs Session Tokens
- SAML
- API Keys
- Session Management
- Cookie Security (SameSite, HttpOnly, Secure)
- CORS
- CSRF
- XSS
- SQL Injection
- IDOR (Insecure Direct Object Reference)
- Mass Assignment
- OWASP Top 10
- OWASP API Security Top 10
- Rate Limiting & Throttling
- Input Validation & Sanitisation
- Secret Management (Vault, AWS Secrets Manager)
- mTLS (Mutual TLS)
- Zero Trust Architecture
- DDoS Protection
- Bot Detection & CAPTCHA
- Content Security Policy (CSP)
- HSTS (HTTP Strict Transport Security)
- Penetration Testing Concepts
- Principle of Least Privilege
- Role-Based Access Control (RBAC)
- Attribute-Based Access Control (ABAC)
- Threat Modelling
- Secure SDLC
- Vulnerability Management
- Security Headers
- Supply Chain Security
- SBOM
- SAST
- DAST
- IAST
- Dependency Scanning
- Secrets Scanning
- Data Privacy
- Data Classification
- Data Retention
- Data Residency
- GDPR
- SOC 2
- PCI DSS

---

## 10. Databases — Fundamentals

- Relational Databases (RDBMS)
- SQL Basics
- Normalisation (1NF – 3NF, BCNF)
- Denormalisation
- Indexes (B-Tree, Hash, Composite, Covering, Partial, Full-text)
- Transactions
- ACID Properties
- Isolation Levels (Read Uncommitted, Read Committed, Repeatable Read, Serialisable)
- Joins, Views, Stored Procedures, Triggers
- Query Optimisation & EXPLAIN Plans
- Entity-Relationship (ER) Modelling
- Foreign Keys & Referential Integrity
- Constraints
- Materialised Views
- Stored Function Design
- Query Plan Caching
- Index Maintenance
- Database Statistics

---

## 11. Databases — Advanced & Patterns

- NoSQL (Document, Key-Value, Column-Family, Graph)
- OLTP vs OLAP
- Row-Oriented vs Column-Oriented Databases
- CAP Theorem
- PACELC Theorem
- BASE Properties
- Weak Consistency
- Eventual Consistency
- Strong vs Eventual vs Causal Consistency
- Read/Write Quorum
- MVCC (Multi-Version Concurrency Control)
- Database Locking (Optimistic vs Pessimistic)
- Deadlocks
- Connection Pooling
- Time-Series Databases
- Full-Text Search (Elasticsearch, Solr)
- Graph Databases (Neo4j)
- NewSQL Databases
- Database Federation
- Change Data Capture (CDC)
- Database Migration Strategies
- Schema Versioning (Flyway, Liquibase)
- Database Replication Lag
- Hot Standby vs Warm Standby vs Cold Standby
- Database per Service Pattern
- Shared Database Anti-Pattern
- Multi-Tenancy Data Models
- Online Schema Changes
- Data Archiving
- Database Vacuuming
- Tombstones

---

## 12. Caching

- Cache Concepts (hit, miss, eviction)
- Cache Strategies (Cache-Aside, Write-Through, Write-Behind, Read-Through)
- Cache Invalidation
- Cache Eviction Policies (LRU, LFU, FIFO, ARC)
- TTL (Time-To-Live)
- CDN (Content Delivery Network)
- CDN Push vs Pull
- Edge Caching
- Browser Caching
- In-Memory Caches (Redis, Memcached)
- Redis Data Structures
- Distributed Cache
- Cache Stampede / Thundering Herd
- Hotspot Problem
- Negative Caching
- Cache Warming
- Cache Coherence
- Write Coalescing
- Request Collapsing

---

## 13. Concurrency & Parallelism

- Concurrency vs Parallelism
- Threads vs Processes
- Thread Safety
- Race Conditions
- Deadlocks & Livelocks
- Mutex, Semaphore, Monitor
- Spinlock
- Read-Write Lock
- Atomic Operations
- Memory Barriers & Visibility
- Thread Pooling
- Event Loop
- Async I/O & Non-blocking I/O
- Coroutines & async/await
- Actor Model
- Reactive Programming (Reactive Streams)
- Backpressure
- Fork-Join Model
- Green Threads vs OS Threads
- Structured Concurrency
- Lock-Free Data Structures
- Wait-Free Data Structures
- Work Stealing

---

## 14. Rate Limiting & Traffic Management

- Token Bucket Algorithm
- Leaky Bucket Algorithm
- Fixed Window Counter
- Sliding Window Log
- Sliding Window Counter
- Distributed Rate Limiting
- Request Throttling
- Client-Side Rate Limiting
- Quota Management
- Adaptive Rate Limiting
- Load Shedding
- Admission Control
- Traffic Shaping

---

## 15. Scalability

- Vertical Scaling (Scale Up)
- Horizontal Scaling (Scale Out)
- Load Balancing (Round Robin, Least Connections, IP Hash, Weighted)
- Layer 4 vs Layer 7 Load Balancing
- Global Server Load Balancing (GSLB)
- Session Stickiness
- Auto-Scaling (reactive vs predictive)
- Stateless Service Design
- Database Read Replicas
- Database Sharding (Range, Hash, Directory-based)
- Consistent Hashing
- Data Partitioning Strategies
- Hotspot Mitigation
- Geo-Distributed Systems
- Cell-Based Architecture
- Control Plane vs Data Plane
- Multi-Tenancy
- Tenant Isolation
- Noisy Neighbour Problem

---

## 16. Reliability & Fault Tolerance

- Single Point of Failure (SPOF)
- Redundancy & Replication
- Failover (Active-Passive, Active-Active)
- Circuit Breaker Pattern
- Retry & Exponential Backoff with Jitter
- Bulkhead Pattern
- Timeout Strategies
- Graceful Degradation
- Fallback Strategies
- Chaos Engineering
- Health Checks & Readiness / Liveness Probes
- Disaster Recovery (RTO, RPO)
- Backup & Restore Strategies
- Fencing Tokens
- Idempotency Keys
- Error Budgets
- Fault Injection
- Brownout Strategy
- Degraded Mode
- Runbooks
- Incident Management
- Postmortems

---

## 17. Distributed Systems — Concepts

- Fallacies of Distributed Computing
- Two Generals Problem
- Byzantine Generals Problem
- Distributed Systems Challenges
- Clocks & Time (Physical, Logical, Vector Clocks)
- Lamport Timestamps
- Consensus Algorithms (Paxos, Raft)
- Leader Election
- Split Brain Problem
- Two-Phase Commit (2PC)
- Three-Phase Commit (3PC)
- Distributed Transactions
- Saga Pattern (Choreography vs Orchestration)
- Gossip Protocol
- Quorum-Based Systems
- Replication Strategies (Synchronous, Asynchronous, Semi-synchronous)
- Distributed Locks
- Lease-Based Coordination
- Causal Ordering
- Total Ordering
- Exactly-Once Processing
- Network Partitions
- Failure Detectors

---

## 18. Distributed Systems — Algorithms & Data Structures

- Bloom Filters
- HyperLogLog
- Count-Min Sketch
- Merkle Trees
- Consistent Hashing (ring-based)
- Rendezvous Hashing
- B-Trees & LSM Trees (storage internals)
- Skip Lists
- CRDTs (Conflict-free Replicated Data Types)
- Write-Ahead Log (WAL)
- Compaction & SSTables
- Trie
- Radix Tree
- Rope
- B+ Tree
- Log-Structured Merge Tree

---

## 19. Messaging & Async Communication

- Synchronous vs Asynchronous Communication
- Message Queues
- Message Bus / Message Broker
- Pub/Sub Pattern
- Producer / Consumer Pattern
- Point-to-Point Messaging
- Fan-Out Pattern
- Dead Letter Queues (DLQ)
- Message Idempotency
- At-Least-Once / At-Most-Once / Exactly-Once Delivery
- Message Ordering & Sequencing
- Poison Message Handling
- RabbitMQ
- Apache Kafka (topics, partitions, consumer groups, offsets)
- Kafka Connect & Kafka Streams
- Schema Registry
- Amazon SQS / SNS
- Azure Service Bus
- Google Pub/Sub
- NATS
- Apache Pulsar
- Redis Streams
- Transactional Messaging
- Message Deduplication

---

## 20. Event-Driven Architecture

- Events vs Commands vs Queries
- Event-Driven Architecture (EDA)
- Event Sourcing
- CQRS (Command Query Responsibility Segregation)
- Outbox Pattern
- Inbox Pattern
- Event Schema Evolution
- Event Store
- Domain Events
- Event Replay
- Competing Consumers Pattern
- Priority Queue Pattern
- Materialised View Pattern
- Temporal Query Pattern
- Process Manager Pattern

---

## 21. Data Engineering & Streaming

- ETL vs ELT
- Data Warehousing
- Data Lake
- Data Lakehouse
- OLAP vs OLTP
- Column-Oriented Databases
- Batch Processing
- Stream Processing
- Lambda Architecture
- Kappa Architecture
- Apache Spark (batch)
- Apache Flink (streaming)
- Change Data Capture (CDC)
- Data Pipelines
- Backfilling
- Exactly-Once Semantics in Streams
- Watermarks & Late Data
- Data Mesh
- Data Contracts
- Data Quality
- Data Lineage
- Data Governance
- Slowly Changing Dimensions

---

## 22. Microservices

- Monolith vs Microservices vs SOA
- Microservice Decomposition (by business capability, by subdomain)
- Bounded Context
- Inter-Service Communication (sync vs async)
- Service Discovery (client-side vs server-side)
- Service Registry (Consul, Eureka, etcd)
- API Gateway
- Backend for Frontend (BFF)
- Service Mesh (Istio, Linkerd)
- Strangler Fig Pattern
- Sidecar Pattern
- Ambassador Pattern
- Data Isolation per Service
- Distributed Tracing
- Microservice Testing Strategies
- Contract Testing (Pact)
- Service Ownership
- Platform Teams
- Golden Path
- Service Templates

---

## 23. Domain-Driven Design (DDD)

- Ubiquitous Language
- Domain Model
- Entities & Value Objects
- Aggregates & Aggregate Roots
- Repositories
- Domain Services
- Application Services
- Bounded Contexts
- Context Mapping
- Anti-Corruption Layer
- Strategic vs Tactical DDD
- Shared Kernel
- Open Host Service
- Published Language
- Customer-Supplier Context
- Conformist Context
- Separate Ways

---

## 24. API Design & Management

- API Design Principles
- RESTful Resource Naming
- Pagination (Offset, Cursor-based, Keyset)
- Filtering, Sorting, Searching
- API Documentation (OpenAPI / Swagger)
- API Gateway Patterns
- API Deprecation Strategies
- Backwards Compatibility
- Breaking vs Non-Breaking Changes
- API Mocking
- API Testing
- API Lifecycle Management
- API Governance
- API Analytics
- Developer Portals
- SDK Design
- Error Response Design

---

## 25. Networking & Infrastructure

- Reverse Proxy vs Forward Proxy
- Nginx / HAProxy
- VPN & Tunnelling
- Firewalls & Security Groups
- NAT (Network Address Translation)
- Anycast
- BGP Basics
- Long-lived Connections
- Connection Draining
- VLAN
- Virtual Machines & Hypervisors
- Containers vs VMs
- VPC
- Subnets
- Route Tables
- Internet Gateway
- NAT Gateway
- PrivateLink
- DNS Load Balancing
- TLS Termination
- WAF

---

## 26. Storage & File Systems

- Block Storage vs Object Storage vs File Storage
- Amazon S3 / Blob Storage Concepts
- File Upload Strategies (direct, presigned URL, multipart)
- Data Compression (gzip, snappy, lz4, zstd)
- Data Encryption at Rest & in Transit
- Backup Strategies
- Archival Storage (cold/warm/hot tiers)
- RAID
- Distributed File Systems (HDFS, GlusterFS)
- Erasure Coding
- Storage Replication
- Storage Tiering
- Data Lifecycle Management
- Checksumming

---

## 27. Observability & Monitoring

- Logging (Structured Logging, Log Levels)
- Metrics (RED: Rate, Errors, Duration; USE: Utilisation, Saturation, Errors)
- Distributed Tracing (OpenTelemetry, Jaeger, Zipkin)
- Alerting & On-Call
- Dashboards (Grafana, Datadog)
- Log Aggregation (ELK Stack, Splunk)
- Error Tracking (Sentry)
- Audit Logs
- Correlation IDs
- Continuous Profiling
- APM (Application Performance Monitoring)
- SLO-Based Alerting
- Log Sampling
- Trace Sampling
- Metric Cardinality
- Synthetic Monitoring
- Real User Monitoring
- Black-Box Monitoring
- White-Box Monitoring
- Service Catalogues

---

## 28. Testing

- Unit Testing
- Integration Testing
- End-to-End Testing
- Contract Testing (Consumer-Driven, Pact)
- Component Testing
- Load Testing & Stress Testing
- Performance Testing
- Smoke Testing
- Chaos Testing
- Test Doubles (Mocks, Stubs, Fakes, Spies)
- TDD (Test-Driven Development)
- BDD (Behaviour-Driven Development)
- Test Pyramid
- Mutation Testing
- Snapshot Testing
- Regression Testing
- Compatibility Testing
- Security Testing
- Usability Testing
- Accessibility Testing
- Visual Regression Testing
- Property-Based Testing
- Fuzz Testing
- Soak Testing

---

## 29. DevOps & Deployment

- CI/CD Pipelines
- Blue-Green Deployment
- Canary Deployment
- Rolling Deployment
- Shadow Deployment
- Feature Flags
- Infrastructure as Code (Terraform, CloudFormation)
- Configuration Management (Ansible, Chef, Puppet)
- Immutable Infrastructure
- Containerisation (Docker)
- Container Orchestration (Kubernetes)
- Helm Charts
- Service Accounts & RBAC in Kubernetes
- Network Policies in Kubernetes
- Secrets in Kubernetes
- GitOps (ArgoCD, Flux)
- Artifact Management
- Release Management
- Environment Promotion
- Deployment Gates
- Container Image Scanning
- Policy as Code
- Build Reproducibility
- Monorepos
- Trunk-Based Development

---

## 30. Cloud Architecture

- Cloud Providers Overview (AWS, GCP, Azure)
- Regions & Availability Zones
- Multi-Region Architecture
- Cloud-Native Design Principles
- Managed Services vs Self-Hosted
- Serverless Architecture
- Function as a Service (FaaS)
- Event-Driven Serverless
- Cost Optimisation Strategies
- Shared Responsibility Model
- FinOps
- Cloud Security Posture Management (CSPM)
- Well-Architected Framework (AWS/Azure/GCP)
- IAM
- KMS
- VPC Peering
- Transit Gateway
- Private Endpoints
- Landing Zones
- Cloud Networking
- Cloud Cost Allocation

---

## 31. Frontend Architecture

- Single Page Application (SPA)
- Multi-Page Application (MPA)
- Server-Side Rendering (SSR)
- Static Site Generation (SSG)
- Incremental Static Regeneration (ISR)
- Progressive Web Apps (PWA)
- Micro-frontends
- Module Federation
- Client-Side Routing
- State Management (Redux, Zustand, MobX)
- Browser Storage (LocalStorage, SessionStorage, IndexedDB)
- Service Workers
- Web Performance (Core Web Vitals, TTFB, LCP, CLS)
- Code Splitting & Lazy Loading
- Tree Shaking
- Critical Rendering Path
- Accessibility
- Internationalisation
- Localisation
- Design Systems
- Component Libraries
- Hydration
- Edge Rendering
- Browser Security
- Offline-First Architecture

---

## 32. Workflow & Job Orchestration

- Cron Jobs
- Distributed Job Schedulers
- Workflow Orchestration (Temporal, Conductor, Airflow)
- Long-Running Workflows
- Saga Orchestration
- Human-in-the-Loop Workflows
- Idempotent Job Execution
- Job Retries & Dead-Letter
- Priority Queues for Jobs
- Rate-Limited Job Processing
- Job Leasing
- Job Checkpointing
- Workflow Versioning
- Workflow Compensation
- Distributed Cron

---

## 33. Capacity Planning & Estimation

- Back-of-the-Envelope Calculations
- Traffic Estimation Techniques
- Storage Estimation
- Bandwidth Estimation
- Read/Write Ratio Analysis
- Peak vs Average Load
- Growth Projections
- Cost Estimation
- Headroom Planning
- Capacity Modelling
- Saturation Points
- Queueing Theory
- Little's Law
- Forecasting

---

## 34. System Design Case Studies (Apply All Above)

- URL Shortener
- Rate Limiter
- Chat Application
- Notification System
- News Feed / Timeline
- File Storage Service (Dropbox/S3-like)
- Video Streaming Service
- Search Autocomplete / Typeahead
- Ride-Sharing System
- Payment System
- Distributed Job Scheduler
- Key-Value Store
- Distributed Cache (Redis-like)
- Web Crawler
- Leaderboard / Ranking System
- E-Commerce Cart & Checkout
- Hotel/Flight Reservation System
- Ad Click Aggregator
- Live Commenting System
- Distributed Message Queue (Kafka-like)
- API Gateway
- Monitoring & Alerting System
- Collaborative Editor (Google Docs-like)
- Proximity Service (Yelp / Nearby)
- Ticketmaster / High Concurrency Booking
- Stock Exchange Matching Engine
- Top-K Heavy Hitters (Metrics Aggregation)
- Pastebin / Image Hosting
- Flash Sale / Inventory Management
- Authentication System
- Subscription Billing System
- Multi-Tenant SaaS Platform
- Logging Pipeline
- Metrics Platform
- Feature Flag Platform
- Configuration Service
- Audit Logging System
- Email Delivery Platform
- Real-Time Analytics Dashboard

---

## 35. Information Retrieval & Core Algorithms

- Inverted Index
- TF-IDF & BM25
- PageRank
- Spatial Indexes (QuadTree, R-Tree, Geohash)
- Operational Transformation (OT) / CRDTs
- Tokenisation
- Stemming
- Lemmatization
- Ranking
- Relevance Tuning
- Faceted Search

---

## 36. Advanced Hardware & Storage

- Memory Hierarchy (L1, L2, L3, RAM)
- SSD vs HDD vs NVMe Latency/IOPS
- Hardware Security Modules (HSM)
- CPU Cache Locality
- NUMA
- SIMD
- Kernel Bypass
- Direct Memory Access

---

## 37. Networking & Performance Extensions

- Edge Computing
- Hardware vs Software Load Balancers
- Peer-to-Peer Networks (P2P)
- Zero-copy (sendfile)
- eBPF (kernel-level observability & networking)
- WebAssembly (WASM) at the Edge
- Connection Pool Tuning
- Head-of-Line Blocking
- Nagle's Algorithm
- TCP Slow Start
- TLS Session Resumption
- HTTP Caching Headers

---

## 38. Architecture Practice

- Requirement Gathering
- Functional Requirements
- Non-Functional Requirements
- Quality Attributes
- Trade-Off Analysis
- C4 Model
- UML
- Sequence Diagrams
- Component Diagrams
- Deployment Diagrams
- Architecture Reviews
- Technical Debt Management
- Migration Planning
- Build vs Buy Decisions

---

## 39. Platform Engineering & SRE

- Developer Experience
- Internal Developer Platforms
- Self-Service Infrastructure
- Service Catalogue
- Golden Paths
- Toil Reduction
- Reliability Reviews
- Production Readiness Reviews
- Error Budget Policies
- Operational Excellence
- Capacity Reviews
- Game Days

---

## 40. Mobile & Client Architecture

- Native Apps
- Cross-Platform Apps
- Offline Sync
- Push Notifications
- App Versioning
- Mobile Networking
- Battery-Aware Design
- Local Persistence
- Background Jobs
- App Store Release Management
- Deep Linking
- Crash Reporting
