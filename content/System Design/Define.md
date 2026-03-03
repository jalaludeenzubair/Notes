| Feature               | TLS over TCP        | QUIC / HTTP/3     |
| --------------------- | ------------------- | ----------------- |
| Transport             | TCP                 | UDP               |
| Handshake Speed       | 2–3 RTT             | 0–1 RTT           |
| Head-of-Line Blocking | Yes                 | No                |
| Connection Migration  | No                  | Yes               |
| Upgrade Speed         | Slow (OS dependent) | Fast (user-space) |
| Encryption            | TLS layered         | TLS 1.3 built-in  |

---

In QUIC (used by HTTP/3), a single connection supports multiple independent streams, such as HTML, CSS, JavaScript, and images. If packet loss occurs in one stream (for example, CSS), only that particular stream is affected while the others continue transmitting data normally. This eliminates the Head-of-Line blocking problem seen in TCP, where one lost packet can block the entire connection. Additionally, QUIC uses a Connection ID instead of relying on the client’s IP address. This allows connection migration—if a user switches from WiFi to mobile data and the IP address changes, the connection continues without restarting. As a result, QUIC provides faster performance, better reliability, and improved user experience, especially on mobile networks.

---

If there is a Partition (P), choose between Availability (A) and Consistency (C); Else (E), choose between Latency (L) and Consistency (C).

If Partition → A or C
Else → L or C

Clock Skew : Machines disagree on time → timestamps unreliable.

Monotonic Reads : You never go backward in what you see.

Causal Consistency : You never see effect before cause.

Vector Clocks : Track logical version history to detect concurrent updates.

CRDTs : Design data structures so conflicts merge automatically.

---

Write Path (Step-by-Step)

- Write goes to a WAL (Write-Ahead Log) for durability.
- Write goes into the Memtable.
- Memtable fills up.
- Flushed to disk as a new SSTable.
- Background compaction merges SSTables.

Writes are fast because:

- They are sequential.
- No random disk updates.
- No in-place modification.

---

fsync : fsync is a system call that forces the OS to flush buffered file data to disk.

Why it exists

When your program writes to a file:

- The OS usually stores the data in page cache (RAM) first.
- It may delay writing to disk for performance.
- If the system crashes before data reaches disk → data loss.

fsync(fd) tells the OS: “Make sure everything written to this file descriptor is physically persisted to disk.”

---

| Feature         | L4          | L7                          |
| --------------- | ----------- | --------------------------- |
| Speed           | Very fast   | Slower                      |
| Routing logic   | IP + Port   | Content-aware               |
| TLS termination | Usually no  | Yes                         |
| Smart rules     | No          | Yes                         |
| Best for        | High volume | Intelligent traffic control |

---

1. Lagging Indicator (Latency)
   What it is: Metric that shows problems after they happen.
   Example: Slow app response (users already affected).
   Analogy: Engine is already smoking → too late to prevent damage.
2. Leading Indicator (Saturation)
   What it is: Metric that predicts problems before they happen.
   Example: CPU, memory, or database pool almost full.
   Analogy: Fuel gauge showing low fuel → warning before running out.
3. Saturation = Fuel Gauge
   Shows how close a system resource is to its limit.
   High saturation → system is at risk of failure.
   Acting on it prevents latency spikes.
4. Latency = Pain Users Feel
   Measures how slow the system is.
   Latency rises after saturation is high.
   It’s reactive, not predictive.
5. Proactive vs. Reactive
   Proactive: Watch saturation → act before users feel problems.
   Reactive: Watch latency → fix after users complain.
   Goal: Prevent cascading failures by acting early.

---

1. Parallelizable vs Serial Code
   • In software, some tasks can run in parallel (simultaneously) across multiple threads, cores, or servers.
   Examples: processing multiple user requests, batch data processing, rendering multiple images.
   • Some tasks are serial (must happen step by step).
   Examples: writing to a single database row, acquiring a global lock, or initializing configuration.
   Key point: The serial part cannot be sped up by adding more threads or servers.
2. Maximum Speedup in Software
   Amdahl’s Law tells you the upper limit of speedup when you parallelize your software:
   If 5% of your code is serial, even if you run the parallel 95% on hundreds of servers, the fastest your program can ever run is 20× faster.
   The serial portion becomes the bottleneck.

Purpose: Predicts the maximum speedup of a task when part of it can be parallelized.

Formula:

Speedup(n) = 1 / ( S + (P / n) )
