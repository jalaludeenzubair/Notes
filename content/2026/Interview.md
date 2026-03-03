1. For a Read-Heavy System — Consider using a Cache.
2. For a Write-Heavy System — Use Message Queues for async processing
3. For a Low Latency Requirement — Consider using a Cache and CDN.
4. Need 𝐀tomicity, 𝐂onsistency, 𝐈solation, 𝐃urability Compliant DB — Go for RDBMS/SQL Database.
5. Have unstructured data — Go for NoSQL Database.
6. Have Complex Data (Videos, Images, Files) — Go for Blob/Object storage.
7. Complex Pre-computation — Use Message Queue & Cache.
8. High-Volume Data Search — Consider search index, tries, or search engine.
9. Scaling SQL Database — Implement Database Sharding.
10. High Availability, Performance, & Throughput — Use a Load Balancer.
11. Global Data Delivery — Consider using a CDN.
12. Graph Data (data with nodes, edges, and relationships) — Utilize Graph Database.
13. Scaling Various Components — Implement Horizontal Scaling.
14. High-Performing Database Queries — Use Database Indexes.
15. Bulk Job Processing — Consider Batch Processing and Message Queues.
16. Server Load Management & Preventing DOS Attacks- Use a Rate Limiter.
17. Microservices Architecture — Use an API Gateway.
18. For Single Point of Failure — Implement Redundancy.
19. For Fault-Tolerance and Durability — Implement Data Replication.
20. For User-to-User fast communication — Use Websockets.
21. Failure Detection in Distributed Systems — Implement a Heartbeat.
22. Data Integrity — Use Checksum Algorithm.
23. Efficient Server Scaling — Implement Consistent Hashing.
24. Decentralized Data Transfer — Consider Gossip Protocol.
25. Location-Based Functionality — Use Quadtree, Geohash, etc.
26. Avoid Specific Technology Names — Use generic terms.
27. High Availability and Consistency Trade-Off — Eventual Consistency.
28. For IP resolution and domain Name Query — Mention DNS.
29. Handling Large Data in Network Requests — Implement Pagination.
30. Cache Eviction Policy — Preferred is LRU (Least Recently Used) Cache.
31. To handle traffic spikes: Implement Autoscaling to manage resources dynamically
32. Need analytics and audit trails — Consider using data lakes or append-only databases
33. Handling Large-Scale Simultaneous Connections — Use Connection Pooling and consider using Protobuf to minimize data payload

---

### 1. Database Scaling and Partitioning

The notes detail how companies move beyond a single monolithic database as they hit storage and connection limits.

- **Vertical Partitioning (Federation):**
  - **Shopify** and **Figma** initially scaled by splitting their primary database into separate parts based on table groups (e.g., moving distinct tables to different databases).
  - **Benefit:** Relieves pressure on the primary DB without the complexity of sharding immediately.
- **Horizontal Sharding:**
  - **Figma, Notion, and Stripe** utilize horizontal sharding, where data is distributed across nodes based on a **Shard Key** (e.g., UserID, FileID, OrgID).
  - **Logical vs. Physical Sharding:** Figma implemented **Logical Sharding** (application layer organization) first, followed by **Physical Sharding** (actual distribution across servers).
  - **Database Proxies:** Custom proxies (often written in Go) are used to parse SQL, determine the shard ID, and route the query to the correct physical database. This abstracts complexity from the application layer.
- **Time-Based Partitioning:**
  - **Zerodha** splits databases by financial year since historical data is immutable.
  - **Netflix** shards viewing history by age (Recent, Past, Historical clusters) to optimize for different access patterns.

### 2. Database Migration Strategies

The notes cover how to migrate databases with zero downtime and high data integrity.

- **Dual-Writing:** Writing to both the old and new databases simultaneously during migration (Notion, Discord).
- **Backfilling:** Migrating historical data while dual-writes handle new incoming traffic.
- **Verification:** Ensuring data integrity before switching read traffic to the new system.
- **Custom Tooling:** Discord built a custom migrator in Rust (rather than using Spark) to reduce migration time from 3 months to 9 days.

### 3. Caching Architectures

A significant portion of the notes is dedicated to caching strategies to reduce latency and database load.

- **Layered Caching:**
  - **DoorDash** uses a 3-layer approach: Request Local (HashMap) → Local Cache (Caffeine) → Remote Cache (Redis).
- **Cache Invalidation:**
  - **CDC (Change Data Capture):** Uber and DoorDash use CDC events from the database to trigger cache invalidation, ensuring consistency.
  - **Consistency Monitoring:** **Facebook** uses a service called "Polaris" to actively monitor and detect inconsistencies between the cache and the database.
- **Global Replication & Efficiency:**
  - **Netflix EVCache:** Implements a "Metadata-only" replication strategy. Instead of sending the full data payload across regions, they send metadata, and the remote region fetches the data locally or re-computes it, saving bandwidth.
  - **Hybrid Storage (RAM + SSD):** Netflix uses **Memcached extstore** to store hot data in RAM and warm data on NVMe SSDs, reducing costs by ~55%.
- **Cache Warming:**
  - **Uber** handles region failovers by replicating Redis write streams to remote regions to keep caches warm.
  - **Netflix** scales clusters instantly by taking snapshots of existing nodes and restoring them to new nodes, bypassing the need to wait for TTL expiration.

### 4. Handling High-Concurrency & "Hot" Data

Specific strategies for dealing with traffic spikes and uneven data access.

- **Hot Partitions:**
  - **Discord** faced "Hot Partitions" when high-traffic channels (like those with `@everyone` mentions) overloaded specific database nodes.
  - **Request Coalescing:** To solve this, Discord built a Data Services layer (in Rust) that coalesces multiple identical user requests into a single database query.
- **Tiered Storage Optimization:**
  - **Netflix** separates "Live" viewing history (uncompressed, fast writes) from "Compressed" history (slow writes, high storage efficiency).
  - **Intelligent Filtering:** Systems filter out low-value data (e.g., Netflix not storing video previews watched for only a few seconds) to save space.

### 5. Real-Time Communication

The notes explore architectures for live updates and collaboration.

- **WebSockets vs. WebRTC:**
  - **Canva** initially used WebSockets + Redis for collaborative mouse pointers but faced latency issues. They migrated to **WebRTC** for a Peer-to-Peer (P2P) architecture, allowing clients to communicate directly without server bottlenecks.
- **Message Brokers:**
  - **Trello** moved from RabbitMQ to Kafka because RabbitMQ struggled with "split-brain" issues and connection storms during network partitions.
- **Fanout Models:**
  - **Twitter** uses a "Fanout-on-write" approach for timelines. When a user tweets, the ID is pushed to the Redis cache of all their followers.
  - **Hybrid Approach:** For celebrities (millions of followers), Twitter avoids fanout-on-write and instead uses a "pull" model (fetch on demand) to prevent system overload.

### 6. Operational Excellence & Language Choices

- **Language Selection for Performance:** Discord migrated from Java (Cassandra) to C++ (ScyllaDB) and Rust (Data Services) to eliminate **Garbage Collection (GC) pauses** that were causing latency spikes.
- **Circuit Breakers:** Uber uses sliding window circuit breakers to prevent cascading failures if a Redis node goes down.
- **Priority Queues:** Twitter separates notification traffic into High (login codes), Medium (interactions), and Low (recommendations) priority queues so that a celebrity tweet doesn't block critical system SMS.

### Summary of Key Technologies Mentioned

- **Databases:** MySQL (Vitess), Postgres, MongoDB, Cassandra, ScyllaDB, CockroachDB.
- **Caching:** Redis, Memcached (EVCache), Caffeine.
- **Brokers/Streaming:** Kafka, RabbitMQ.
- **Languages:** Go (Proxy servers), Rust (High-performance tooling), C++ (Database internals).
