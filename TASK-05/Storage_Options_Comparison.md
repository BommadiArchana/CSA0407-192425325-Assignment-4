# Task 5.1 – Compare Distributed and Cloud Storage Options

## Introduction

A university needs a storage system that allows students and staff to access their files from any campus and from home. Three storage options are Network File System (NFS), distributed file systems such as HDFS or Ceph, and cloud object storage such as Amazon S3 or Google Cloud Storage.

## Comparison of Storage Options

| Feature | NFS | Distributed File System (HDFS/Ceph) | Cloud Object Storage |
|---|---|---|---|
| Storage method | Files stored on a central server | Data distributed across multiple storage nodes | Data stored as objects in cloud storage |
| Consistency | Provides shared file access with server-managed consistency | HDFS provides a consistent file-system view; Ceph supports configurable consistency features | Depends on the cloud provider and service |
| Availability | Depends mainly on the NFS server and its backup setup | Replication allows access even if some nodes fail | High availability through cloud infrastructure |
| Performance | Good for shared files over a local network | Supports large-scale storage and parallel access | Depends on internet speed, location and network latency |
| Cost | Requires server hardware and maintenance | Requires multiple servers and administration | Usually uses pay-as-you-go storage and data transfer charges |
| Scalability | Limited by server capacity | Can expand by adding storage nodes | Can scale storage according to demand |
| Suitable use | Campus file sharing | Large distributed data storage | Accessing files from different locations |

## Explanation of Each Storage Option

### 1. Network File System (NFS)

NFS is a network file system that allows users to access files stored on another computer through a network.

**Advantages:**
- Students and staff can share files across the campus network.
- Files can be accessed from different computers.
- Centralised storage makes file management easier.
- Suitable for shared folders and documents.

**Disadvantages:**
- A single NFS server can become a performance bottleneck.
- Server failure may interrupt file access.
- Performance depends on network speed and server capacity.

**Example:** Students can access assignment files stored on a university server from different campus laboratories.

### 2. Distributed File System – HDFS or Ceph

A distributed file system stores data across multiple connected computers or storage nodes.

**Advantages:**
- Data can be stored across multiple machines.
- Replication protects data against individual node failures.
- Storage capacity can be increased by adding nodes.
- Supports large amounts of data and multiple users.

**Disadvantages:**
- Requires more hardware and administration.
- Initial setup and maintenance can be complex.
- Network communication between nodes affects performance.

**Example:** A university can store student records across multiple servers so that files remain available even if one storage node fails.

### 3. Cloud Object Storage – Amazon S3 or Google Cloud Storage

Cloud object storage stores files as objects in a cloud service. Each object contains data, metadata and a unique identifier.

**Advantages:**
- Files can be accessed from different locations through the internet.
- Storage capacity can be increased easily.
- The university does not need to maintain all storage hardware.
- Cloud providers offer data durability and availability features.

**Disadvantages:**
- Requires a reliable internet connection.
- Data transfer and storage may involve additional costs.
- Access speed depends on network conditions.
- Access permissions and security must be configured correctly.

**Example:** A student can upload an assignment to cloud storage and access it later from home or another campus.

## Recommended Storage Option for the University

A distributed file system such as Ceph is a suitable option when the university wants shared storage across campuses, increasing storage capacity and protection through replication.

Cloud object storage can also be used for backups and files that need access from different locations.

NFS is suitable for smaller campus networks where centralised file sharing is sufficient.

## Conclusion

NFS provides simple centralised file sharing, distributed file systems provide scalability and replication, and cloud object storage provides access from different locations without maintaining all storage hardware. The university should select the system according to its number of users, performance requirements, availability needs and budget.
