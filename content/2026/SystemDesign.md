| Feature                   | Fanout        | Direct            | Topic             |
| ------------------------- | ------------- | ----------------- | ----------------- |
| Uses routing key?         | :x: No        | ✅Exact match     | ✅Pattern match   |
| Broadcasts to all queues? | ✅ Yes        | :x: No            | :x: No            |
| Flexible routing?         | :x: No        | :warning: Limited | ✅ Very flexible  |
| Common use                | Notifications | Log routing       | Complex filtering |

| Aspect                   | MCP (Model-Centric Programming)                                       | Function Calling                                   |
| ------------------------ | --------------------------------------------------------------------- | -------------------------------------------------- |
| **User Query**           | User sends a query (e.g., weather question)                           | User sends a query                                 |
| **Who chooses tool?**    | MCP Client chooses the appropriate tool (e.g., Weather API)           | Function call is explicitly declared in prompt     |
| **API Request Approval** | MCP requests user approval before calling API                         | No explicit approval step shown                    |
| **Where is the logic?**  | MCP Client + LLM (Large Language Model) handle logic & tool selection | Application triggers function call                 |
| **Interaction Flow**     | User → MCP Client → MCP Server → External API → LLM → Output          | User → Function Call → External API → LLM → Output |
| **Response Handling**    | MCP Client aggregates data and generates final output                 | Function call returns data directly                |
| **Architecture Type**    | More complex, involves multiple components (client, server, LLM)      | Simpler, direct function calls                     |
| **Use Case**             | Flexible tool selection with user approval                            | Streamlined function calls in applications         |

---

**SSH (Secure Shell)** is a **network protocol** that allows secure communication between a client and a remote server

![](assets/20260214_195406_image.png)

---

| Feature     | Cookies                  | Sessions                | JWT                                     |
| ----------- | ------------------------ | ----------------------- | --------------------------------------- |
| Storage     | Client browser           | Server memory / DB      | Client (localStorage / cookie)          |
| Stateless   | ❌                       | ❌                      | ✅                                      |
| Security    | HttpOnly, Secure         | Server-controlled       | Signature, expiry, secure transport     |
| Scalability | ✅                       | ❌ (needs shared store) | ✅                                      |
| Revocation  | ❌                       | ✅ easy                 | ❌ tricky                               |
| Typical Use | Preferences, simple auth | Traditional login       | Modern APIs, mobile apps, microservices |

---

|                                     | API Gateway                                         | Reverse Proxy                        | Load Balancer                       |
| ----------------------------------- | --------------------------------------------------- | ------------------------------------ | ----------------------------------- |
| **Primary Responsibility**          | API management & policy enforcement                 | Traffic forwarding & edge protection | Traffic distribution & availability |
| **Layer (OSI)**                     | L7 (Application layer)                              | Mostly L7 (can work at L4)           | L4 or L7                            |
| **Understands APIs?**               | ✅ Yes (routes by path, version, headers)           | ⚠️ Limited                           | ❌ No (unless L7 LB)                |
| **Authentication / Authorization**  | ✅ Full support (JWT, OAuth, API keys)              | ⚠️ Basic (headers, IP filtering)     | ❌ Not responsible                  |
| **Rate Limiting / Throttling**      | ✅ Built-in                                         | ⚠️ Limited                           | ❌ No                               |
| **Load Balancing**                  | ⚠️ Sometimes built-in                               | ✅ Yes (basic)                       | ✅ Core responsibility              |
| **Health Checks**                   | ⚠️ Optional                                         | ✅ Yes                               | ✅ Yes                              |
| **Request/Response Transformation** | ✅ Yes                                              | ⚠️ Limited                           | ❌ No                               |
| **Caching**                         | ⚠️ Sometimes                                        | ✅ Yes                               | ❌ No                               |
| **Service Aggregation**             | ✅ Yes (calls multiple services)                    | ❌ No                                | ❌ No                               |
| **Use in Microservices**            | ✅ Central entry point                              | ⚠️ Edge layer                        | ✅ For scaling services             |
| **Failure Handling**                | Circuit breakers, retries                           | Basic retries                        | Failover to healthy instances       |
| **Complexity**                      | High                                                | Medium                               | Low                                 |
|                                     | Public APIs, mobile backend, microservices security | Web server setup, SSL termination    | Scaling & high availability         |

---

**CQRS** (**Command Query Responsibility Segregation**)

- CQRS = Separate **Commands (write)** and **Queries (read)**
- **Command** : Changes data (create, update, delete). Has business rules.
- **Query** : Only reads data. No state change.
- **Why** : Read and write have different logic and scaling needs.
- **In Practice** : Use separate **Command Service** and **Query Service** in production (don’t over-engineer).

---

| Feature        | Data Lake                               | Append-Only Database                 |
| -------------- | --------------------------------------- | ------------------------------------ |
| Purpose        | Analytics / historical data exploration | Audit trails / event sourcing        |
| Data type      | Raw, structured & unstructured          | Structured events only               |
| Writes         | Can overwrite/append                    | Only append (no updates/deletes)     |
| Access Pattern | Batch processing, analytics queries     | Transactional or replay queries      |
| Examples       | AWS S3, Azure Data Lake, HDFS           | MongoDB append-only, Cassandra, QLDB |

**Data Compression**

- Data compression reduces storage size and transmission bandwidth (Bandwidth is the **maximum amount of data that can be sent over a network connection in a given time**)
- Two main types:
  - Lossless: original data fully recoverable (e.g., JSON, PNG, text files)
  - Lossy: some data lost for higher compression (e.g., JPEG, MP3, video)

- Benefits: faster network transfer, less storage usage, improved performance
- Common algorithms:
  - Lossless: Gzip, Brotli, Deflate, LZ77/LZ78
  - Lossy: JPEG compression, MP3/OGG encoding

---

Implement Consistent Hashing

- Traditional scaling approach: `hash(key) % N`
- When a server is added/removed in modulo hashing, almost all keys get reassigned
- This causes cache invalidation, session loss, data reshuffling, and instability
- Consistent hashing maps both servers and keys onto a hash ring
- Each server is placed on the ring using a hash function
- Each key is also hashed onto the same ring
- A key is assigned to the next clockwise server on the ring
- If no server exists clockwise, the lookup wraps around to the first server (ring behavior)
- When a server is added or removed, only nearby keys are reassigned
- This minimizes redistribution and improves system stability
- Used in distributed systems like Amazon Dynamo
- Used in Apache Cassandra
- Used in Redis Cluster
- Useful for distributed caching, sharding, load balancing, and microservices routing
- Helps achieve horizontal scalability with minimal disruption
- Virtual nodes improve load distribution
- Instead of hashing a server once, hash it multiple times (e.g., ServerA#1, ServerA#2)
- Virtual nodes prevent uneven data distribution
- A strong hash function (MD5/SHA) should be used
- Always implement wrap-around logic in the ring
- Remove unhealthy servers from the ring immediately
- Prefer stateless servers in production (store sessions in shared storage like Redis)
- Major advantage over modulo hashing: only a small subset of keys move during scaling
- Core benefit: reduced cache invalidation and improved fault tolerance
- One-line definition: Consistent hashing distributes keys across servers using a hash ring so that minimal keys move when servers change

---

Network Performance:

This tells you how fast data can move in and out of your instance over the network.

---

There are two approaches:

- Strong Consistency - All servers must return the latest updated value immediately.
- Eventual Consistency - Servers may temporarily return old data,
  but eventually they all become consistent.

---

Think of Stdev as “how much things wiggle around the average”:

- Low Stdev → responses are consistently around the average
- High Stdev → responses are all over the place

---

How Data Is Copied to the Secondary in MongoDB

- Client writes to Primary.
- Primary writes to its local storage.
- Primary records operation in its operation log (oplog).
- Secondaries read the oplog.
- Secondaries apply changes asynchronously.

---

Heartbeat Mechanism in Distributed Systems

Each node in a distributed system sends a signal called a heartbeat to a central monitoring system on a regular basis to let it know it is still alive and operating as intended

---

How DNS Works (Step-by-Step):

- User enters domain in browser: example.com.
- Local DNS cache is checked: has IP? Use it.
- If not cached, query goes to DNS recursive resolver (usually your ISP).
- Resolver asks root DNS servers, then TLD servers (like .com), then authoritative DNS servers for the domain.
- Resolver returns the IP address to your computer.
- Browser connects to IP and fetches the website or API.

---

**DB Driver** – App library that connects and communicates with the database

- **DB Proxy (PgBouncer, Mongo Router)** – Manages connection pooling and routing between app and DB
- **Cloud DB Service** – Managed database (AWS RDS, Cloud SQL, Atlas) handles scaling, backups, replication

| Feature            | WebSocket            | Webhook                   | Long Polling      |
| ------------------ | -------------------- | ------------------------- | ----------------- |
| Connection Type    | Persistent           | Per event                 | Repeated requests |
| Direction          | Bi-directional       | One-way (server → server) | Client → server   |
| Real-time          | Yes (true real-time) | Near real-time            | Near real-time    |
| Overhead           | Low after connect    | Low                       | High              |
| Scaling Complexity | High                 | Medium                    | Medium-High       |
| Typical Use        | Chat, live feeds     | Payment events            | Notifications     |

---

**Redundancy-Based Fault-Tolerant Design:**

I identify critical components like application servers, databases, caches, and load balancers, and introduce redundancy at each layer. For applications, I use multiple instances behind a load balancer. For databases, I use replica sets with automatic failover. For caching and queues, I use clustered setups. This ensures no single component failure brings down the entire system.
