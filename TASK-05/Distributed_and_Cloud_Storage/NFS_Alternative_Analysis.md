# Alternative Concept and Complexity Analysis – NFS Server vs Distributed File System

## Introduction

A university can use one large Network File System (NFS) server or a replicated distributed file system to store student and staff files. Both systems provide shared storage, but they differ in performance, storage requirements and availability.

## 1. One Large NFS Server

NFS stores files on a central server and allows users to access them through a network.

**Working:**

1. Students and staff connect to the NFS server.
2. Users send file read and write requests through the network.
3. The NFS server processes the requests.
4. The requested data is returned to the user.

**Advantages:**
- Simple to install and manage.
- Requires fewer storage servers.
- Stores one primary copy of the data.
- Suitable for small and medium-sized environments.

**Disadvantages:**
- A large number of users can overload the server.
- Read and write performance may decrease as requests increase.
- Server failure can interrupt access to files.
- The central server can become a single point of failure.

## 2. Replicated Distributed File System

A distributed file system stores data across multiple storage nodes. Replication maintains multiple copies of data on different nodes.

**Working:**

1. A file is uploaded to the distributed system.
2. The file is divided into blocks.
3. Multiple copies of each block are stored on different nodes.
4. Users access available copies through the distributed system.
5. If a node fails, another available replica can provide the data.

**Advantages:**
- Supports a large number of users.
- Provides better availability through replication.
- Storage capacity can be increased by adding nodes.
- Reduces dependence on a single server.

**Disadvantages:**
- Requires more storage capacity.
- Setup and maintenance are more complex.
- Replication and network communication require additional resources.

## 3. Read and Write Time as Users Increase

| Feature | One Large NFS Server | Replicated Distributed File System |
|---|---|---|
| Read operations | Requests share the same server resources | Reads can be served by multiple available nodes |
| Write operations | Processed through the central server | May require coordination between replicas |
| Increasing users | Server can become overloaded | Workload can be distributed across nodes |
| Performance | May decrease when demand exceeds server capacity | Can improve by adding nodes, depending on workload |

A single NFS server may experience increased response time when many users access files simultaneously. A distributed system can spread read requests across nodes. Write performance depends on the replication and consistency method.

## 4. Storage Used – One Copy vs Three Replicas

Assume the university stores 10 TB of original data.

**NFS Server:**

Storage required = 10 TB

Only one primary copy is stored.

**Distributed File System with Three Replicas:**

Storage required = 10 TB × 3

Storage required = 30 TB

Therefore, three-copy replication requires three times the storage capacity of the original data, excluding additional metadata and system overhead.

## 5. Availability When One Server Fails

**NFS Server:**

If the only NFS server fails, users may lose access to stored files until the server is restored or a backup server takes over.

**Distributed File System:**

If one storage node fails, users may still access the data from another available replica. The system can create a replacement copy to restore the required replication level.

## 6. Comparison Table

| Feature | NFS Server | Distributed File System |
|---|---|---|
| Number of storage servers | Usually one central server | Multiple nodes |
| Storage copies | One primary copy in this comparison | Three replicas in this comparison |
| Storage requirement for 10 TB | 10 TB | 30 TB |
| Read performance | Depends on one server's capacity | Reads can be distributed |
| Write performance | Depends on central server capacity | Depends on replication and coordination |
| Failure handling | Requires backup or failover | Other replicas can provide access |
| Scalability | Limited by central server capacity | Can expand by adding nodes |
| Management | Simpler | More complex |

## 7. Recommended Solution

A replicated distributed file system is more suitable for a large university with students and staff accessing files from different campuses and from home.

It provides better availability and supports increasing storage and user requirements. A three-replica arrangement can protect files when an individual storage node fails.

A single NFS server may be suitable for a smaller university environment where the number of users and storage requirements are limited.

## Conclusion

A single NFS server is simple and requires less storage, but it can become a performance bottleneck and a single point of failure. A replicated distributed file system requires more storage and management, but it provides better scalability and availability. Therefore, a replicated distributed file system is recommended for the university's large-scale storage requirements.
