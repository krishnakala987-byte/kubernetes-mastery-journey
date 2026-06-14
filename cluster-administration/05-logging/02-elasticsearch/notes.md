# Elasticsearch

Purpose:

Store logs centrally.

Features:

- Full text search
- Indexing
- Fast retrieval
- Log storage

Architecture:

Applications
      ↓
Fluent Bit
      ↓
Elasticsearch






# Elasticsearch

## Why Elasticsearch

Elasticsearch is a distributed search and analytics engine used to store, search, and analyze large amounts of data quickly.

### Why do we need it?

Imagine you have millions of logs:

```text
Log 1: User logged in
Log 2: Database connection failed
Log 3: Pod restarted
...
```

Searching through normal files is slow.

Elasticsearch creates indexes that make searching extremely fast.

### Common Use Cases

- Log Management (ELK Stack)
- Application Monitoring
- Full-Text Search
- Security Analytics
- Business Analytics

---

## Cluster

A Cluster is a collection of one or more Elasticsearch nodes working together.

```text
Elasticsearch Cluster
│
├── Node 1
├── Node 2
└── Node 3
```

### Easy Memory Trick

Cluster = Team of Elasticsearch Servers

---

## Node

A Node is a single Elasticsearch server.

```text
Server 1 = Node 1
Server 2 = Node 2
Server 3 = Node 3
```

### Easy Memory Trick

Node = One Elasticsearch Machine

---

## Index

An Index is like a database in MySQL.

### MySQL

```text
Database = EmployeeDB
```

### Elasticsearch

```text
Index = employees
```

Examples:

```text
employees
products
orders
logs
```

### Easy Memory Trick

Index = Database

---

## Document

A Document is a single record stored inside an index.

Documents are stored in JSON format.

```json
{
  "name": "Krishna",
  "role": "DevOps Engineer",
  "experience": 2
}
```

### Easy Memory Trick

Document = Row in Database

---

## Shard

A Shard is a small piece of an Index.

When data grows large, Elasticsearch splits the index into multiple shards.

### Without Shards

```text
logs index
└── 1 TB Data
```

### With Shards

```text
logs index
├── Shard 1
├── Shard 2
├── Shard 3
└── Shard 4
```

### Benefits

- Faster Searches
- Better Performance
- Horizontal Scaling

### Easy Memory Trick

Shard = Piece of an Index

---

## Replica

A Replica is a copy of a shard.

Replicas provide:

- High Availability
- Fault Tolerance
- Better Search Performance

```text
Primary Shard 1
Replica Shard 1

Primary Shard 2
Replica Shard 2
```

If a primary shard fails, its replica takes over.

### Easy Memory Trick

Replica = Backup Copy of Shard

---

## Master Nodes

Master Nodes manage the cluster.

Responsibilities:

- Create/Delete Indexes
- Manage Cluster State
- Allocate Shards
- Monitor Cluster Health

```text
Master Node
│
├── Controls Node 1
├── Controls Node 2
└── Controls Node 3
```

### Easy Memory Trick

Master Node = Cluster Manager

---

## Data Nodes

Data Nodes store actual data and process search requests.

Responsibilities:

- Store Documents
- Execute Searches
- Perform Aggregations
- Manage Shards

```text
Data Node 1
├── Shard 1
└── Shard 2

Data Node 2
├── Shard 3
└── Shard 4
```

### Easy Memory Trick

Data Node = Worker Node

---

## Ingest Nodes

Ingest Nodes process data before storing it.

### Incoming Data

```json
{
  "message": "User logged in"
}
```

### Processed Data

```json
{
  "message": "User logged in",
  "timestamp": "2026-06-12",
  "environment": "prod"
}
```

### Common Tasks

- Add Fields
- Remove Fields
- Parse Logs
- Convert Formats

### Easy Memory Trick

Ingest Node = Data Processor

---

## Production Architecture

A typical production Elasticsearch cluster:

```text
                   Applications
                         |
                         |
                   Kibana / APIs
                         |
                         |
                +----------------+
                | Ingest Nodes   |
                +----------------+
                         |
                         |
      --------------------------------------
      |                                    |
      v                                    v

+----------------+               +----------------+
| Data Node 1    |               | Data Node 2    |
| Shard 1        |               | Shard 2        |
| Replica 2      |               | Replica 1      |
+----------------+               +----------------+

          \                       /
           \                     /
            \                   /
             -------------------
                      |
             +----------------+
             | Master Nodes   |
             | (3 Recommended)|
             +----------------+
```

### Recommended Production Setup

| Component | Count |
|------------|--------|
| Master Nodes | 3 |
| Data Nodes | 2+ |
| Ingest Nodes | 1-2 |
| Kibana | 1+ |

---

## Real-World Example

Suppose Flipkart stores product information.

### Cluster

```text
flipkart-cluster
```

### Index

```text
products
```

### Document

```json
{
  "id": 101,
  "name": "iPhone 17",
  "price": 120000
}
```

### Shards

```text
products
├── Shard 1
├── Shard 2
└── Shard 3
```

### Replicas

```text
Shard 1 → Replica 1
Shard 2 → Replica 2
Shard 3 → Replica 3
```

### Nodes

```text
Master Node -> Manages Cluster

Data Node 1 -> Shard 1
Data Node 2 -> Shard 2
Data Node 3 -> Shard 3

Ingest Node -> Processes Product Data
```

---

## Quick Revision

| Term | Remember As |
|--------|-------------|
| Cluster | Team of Nodes |
| Node | Elasticsearch Server |
| Index | Database |
| Document | Row |
| Shard | Piece of Index |
| Replica | Backup Copy |
| Master Node | Cluster Manager |
| Data Node | Worker Node |
| Ingest Node | Data Processor |