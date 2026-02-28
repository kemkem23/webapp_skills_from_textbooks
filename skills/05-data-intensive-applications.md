# Data-Intensive Application Design

**Source:** Designing Data-Intensive Applications (Martin Kleppmann)
**Category:** Core Reading
**Intention:** ออกแบบระบบที่มี database, queue, cache, event, scaling — เข้าใจ trade-off ด้าน reliability/scalability

---

## Key Skills

### 1. Data Models & Query Languages
- Choose the right data model for your use case:
  - **Relational** (SQL) — structured data, complex queries, ACID transactions
  - **Document** (MongoDB, etc.) — flexible schema, nested data, read-heavy
  - **Graph** — highly connected data, relationship-heavy queries
- Understand when to denormalize vs. normalize

### 2. Storage & Retrieval
- Understand storage engine trade-offs:
  - **B-tree** — optimized for reads, used in most relational databases
  - **LSM-tree / SSTable** — optimized for writes, used in Cassandra, RocksDB
- Use indexes wisely — they speed reads but slow writes
- Choose between OLTP (transactional) and OLAP (analytical) storage

### 3. Replication
- **Single-leader** — one writable node, read replicas for scale
- **Multi-leader** — multiple writable nodes, conflict resolution needed
- **Leaderless** — quorum reads/writes, eventual consistency
- Understand replication lag and its effects on read-after-write consistency

### 4. Partitioning (Sharding)
- **Key-range partitioning** — efficient range queries, risk of hotspots
- **Hash partitioning** — even distribution, no range queries
- Handle rebalancing and partition assignment
- Understand secondary index strategies (local vs. global)

### 5. Transactions
- Understand ACID guarantees and what they actually mean
- Know isolation levels: Read Committed, Repeatable Read, Serializable
- Handle concurrent writes: lost updates, write skew, phantoms
- Understand distributed transactions and their costs

### 6. Consistency & Consensus
- **Linearizability** — strongest consistency, highest cost
- **Causal consistency** — respects cause-and-effect ordering
- **Eventual consistency** — weakest guarantee, highest availability
- CAP theorem and its practical implications
- Consensus algorithms (Raft, Paxos) for leader election and coordination

### 7. Stream & Batch Processing
- **Batch processing** — MapReduce, Spark for large-scale data transformations
- **Stream processing** — Kafka, event sourcing for real-time data pipelines
- Combine batch + stream (Lambda / Kappa architecture)
- Event-driven architecture and message broker patterns

### 8. Caching Strategies
- **Cache-aside** — app reads cache first, loads from DB on miss
- **Write-through** — write to cache and DB simultaneously
- **Write-behind** — write to cache, async flush to DB
- Cache invalidation strategies and TTL policies

---

## Practical Application for Web Apps

| Decision | Key Trade-off |
|----------|---------------|
| SQL vs. NoSQL | Schema flexibility vs. query power and ACID |
| Read replicas | Read scalability vs. replication lag |
| Sharding | Write scalability vs. operational complexity |
| Caching | Latency reduction vs. data staleness |
| Message queues | Decoupling vs. eventual consistency |
| Strong vs. eventual consistency | Correctness vs. availability and latency |

---

## Checklist Before Building Data Layer

- [ ] Data model chosen based on access patterns (not hype)
- [ ] Indexing strategy defined for primary query patterns
- [ ] Replication strategy defined (single-leader for most web apps)
- [ ] Caching layer designed with clear invalidation policy
- [ ] Transaction isolation level chosen consciously
- [ ] Backup and recovery procedures planned
- [ ] Data growth projections considered for partitioning needs
- [ ] Event/message patterns identified for async workflows
