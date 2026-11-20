# Replication and Consistency in Distributed Storage

## Introduction

Replication is the process of storing multiple copies of the same data on different servers. It protects data from loss and helps users access files even when one server fails.

## Replication in Distributed File Systems

For example, HDFS can store three copies of a file across different DataNodes.

When a file is uploaded:
1. The first copy is stored on one DataNode.
2. The second copy is stored on another DataNode.
3. The third copy is stored on a different DataNode.

If one server fails, the other copies can still be used to access the data.

## Advantages of Replication

- Protects data from server failures.
- Improves data availability.
- Helps recover lost data.
- Multiple users can access data from different servers.
- Reduces the risk of losing important university files.

## Example of Three-Copy Replication

Assume a university stores a file of 10 GB using three replicas.

Storage required:

10 GB × 3 = 30 GB.

If one server fails, the remaining copies can still provide the file, provided they are available.

## Strong Consistency

Strong consistency means users receive the latest committed data when they read it after a successful update.

**Example:**

A staff member updates a student's marks. When another staff member reads the updated record after the write is confirmed, the latest value is returned.

**Advantages:**
- Users receive updated information.
- Reduces confusion when multiple users access the same record.
- Useful for important records such as student marks and fee details.

**Limitation:**
- Coordination between servers may increase response time.

## Eventual Consistency

Eventual consistency means that updates may take some time to reach all copies. If no new updates occur and communication continues, the copies eventually become consistent.

**Example:**

A student updates a profile photograph. One server may show the new photograph immediately, while another server may show the old photograph for a short time.

**Advantages:**
- Can support faster responses in distributed systems.
- Allows updates to spread between servers without requiring every copy to be updated immediately.

**Limitation:**
- Different users may temporarily see different versions of the data.

## Strong Consistency vs Eventual Consistency

| Factor | Strong Consistency | Eventual Consistency |
|---|---|---|
| Data updates | Latest committed value is returned | Updates may take time to reach all copies |
| Response time | May be higher due to coordination | May be lower in some distributed designs |
| Data differences | Avoids stale reads under the consistency guarantee | Temporary differences are possible |
| Suitable applications | Marks, fees and financial records | Profile photos and less critical shared content |

## Conclusion

Replication protects university data by maintaining multiple copies on different servers. Strong consistency is useful for important records that require the latest confirmed data. Eventual consistency is suitable for data where temporary differences between copies are acceptable. The university should select the consistency method based on the importance of the data and the required response time.
