# Task 5.2 – Replication and Consistency

## Introduction

Replication is the process of storing multiple copies of the same data on different storage nodes. It protects data from loss and improves availability when a storage device or server fails.

## 1. How Replication Protects Data

In a distributed file system such as HDFS, data is divided into blocks and multiple copies of each block are stored on different DataNodes.

For example, if the replication factor is 3, three copies of each data block are maintained.

**Working:**

1. A user uploads a file to the distributed storage system.
2. The file is divided into smaller blocks.
3. Three copies of each block are stored on different DataNodes.
4. If one DataNode fails, the system can access another available copy.
5. The system can create another copy to restore the required replication factor.

**Example:**

Suppose a university stores a student record in three different storage nodes.

- Node 1 stores the first copy.
- Node 2 stores the second copy.
- Node 3 stores the third copy.

If Node 1 fails, the system can retrieve the record from Node 2 or Node 3.

**Advantages of Replication:**

- Protects data against individual node failures.
- Improves data availability.
- Provides backup copies within the distributed system.
- Supports access by multiple users.

## 2. Strong Consistency

Strong consistency means that after a successful write operation, subsequent read operations return the latest committed value according to the system's consistency rules.

**Example:**

A staff member updates a student's address. When another authorised user reads the record after the update has completed, the latest address is returned.

**Advantages:**

- Users receive up-to-date information.
- Reduces conflicting data.
- Suitable for important records and transactions.

**Disadvantage:**

- Coordination between storage nodes may increase response time.
- Some operations may be delayed during network failures.

## 3. Eventual Consistency

Eventual consistency means that updates may take time to reach all replicas. If no new updates occur and communication is restored, the replicas eventually become consistent.

**Example:**

A student updates a profile photo. One server displays the new photo immediately, while another server may display the old photo temporarily. After synchronisation, both servers show the updated photo.

**Advantages:**

- Supports high availability.
- Reduces the need for immediate coordination.
- Useful for applications where temporary differences are acceptable.

**Disadvantages:**

- Different users may temporarily see different versions.
- Applications may need to handle conflicting updates.

## 4. Comparison Between Strong and Eventual Consistency

| Feature | Strong Consistency | Eventual Consistency |
|---|---|---|
| Data updates | Latest committed update is visible to subsequent reads | Updates may take time to reach all replicas |
| Response time | Coordination may increase delay | Often allows faster responses |
| Availability during network problems | Some operations may be delayed or rejected | Some replicas may continue serving requests |
| Data differences | Avoids stale reads under its consistency guarantee | Temporary differences are possible |
| Suitable applications | Banking and important student records | Profile photos and distributed content delivery |

## Conclusion

Replication protects university files by maintaining multiple copies across storage nodes. Strong consistency provides up-to-date information, while eventual consistency allows temporary differences between replicas. The university can choose the consistency method according to the importance of the stored data and its availability requirements.
