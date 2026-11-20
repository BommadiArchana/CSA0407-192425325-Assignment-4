# Implementation Results and Cloud Alternative Analysis

## Stage 5: Workload Simulation and Results

The C program `video_storage_simulation.c` compares two storage designs using 10,000 video access requests.

### Design 1: HDD-Only Storage

All video requests are served from HDD storage. The assumed access latency is 80 milliseconds per request.

### Design 2: HDD with SSD Cache

Popular videos are stored in SSD cache, while less popular videos are served from HDD storage.

- SSD access latency: 10 milliseconds
- HDD access latency: 80 milliseconds
- Popular videos: 100
- Total videos: 1,000
- Popular video requests: 80%
- Other video requests: 20%

### Simulation Results

Run the C program and copy its actual output into the table below. Results may vary depending on the compiler and system.

| Measurement | Design 1: HDD Only | Design 2: HDD + SSD |
|---|---|---|
| Total requests | 10,000 | 10,000 |
| Cache hits | Not applicable | Copy program output |
| Cache misses | Not applicable | Copy program output |
| Average access latency | Copy program output | Copy program output |
| Total access time | Copy program output | Copy program output |

### Observation

The HDD-only design serves every request from hard disk storage. The hybrid design serves popular video requests from SSD cache and other requests from HDD. Therefore, the hybrid design is expected to reduce average access latency and improve video access performance.

The simulation measures assumed storage access latency. It does not measure actual internet streaming speed, network delay, or physical disk reads.

## Cloud Object Storage and CDN Alternative

Another solution is to store videos in cloud object storage and use a Content Delivery Network (CDN) to deliver videos to students.

### Working

1. Videos are uploaded to cloud object storage.
2. The CDN stores frequently requested video content at locations closer to students.
3. When a student requests a video, the CDN checks whether the content is available in its cache.
4. If available, the video is delivered from the CDN.
5. If unavailable, the CDN retrieves it from the cloud storage origin.

### Comparison of Storage Designs

| Factor | Own HDD and SSD Servers | Cloud Storage with CDN |
|---|---|---|
| Storage | Local HDD and SSD servers | Cloud object storage |
| Video delivery | From college servers | From nearby CDN locations |
| Initial investment | Requires hardware purchase | Lower initial hardware investment |
| Scalability | Requires additional servers | Storage and delivery capacity can be increased |
| Maintenance | Managed by the organisation | Mostly managed by the cloud provider |
| Availability | Depends on server setup | Can use multiple cloud locations |
| Cost | Hardware, electricity and maintenance | Storage, requests and data transfer charges |

## Example Capacity and Network Calculation

Assume the platform stores 1,000 videos with an average size of 1 GB.

Total storage required:

1,000 × 1 GB = 1,000 GB = 1 TB.

If 10,000 students watch videos simultaneously at 4 Mbps:

Required bandwidth:

10,000 × 4 Mbps = 40,000 Mbps = 40 Gbps.

For an example monthly transfer calculation, assume each student watches for 2 hours per day for 30 days.

Data used by one student per day:

4 Mbps × 7,200 seconds ÷ 8 = 3,600 MB = 3.6 GB.

Total monthly transfer:

3.6 GB × 10,000 × 30 = 1,080,000 GB.

This is an illustrative workload calculation, not an actual cloud bill. Actual charges depend on the provider, region, CDN cache hit rate, storage size and data transfer pricing.

## Advantages of Cloud Storage with CDN

- Students can access videos from different locations.
- CDN caching reduces repeated requests to the original storage server.
- Storage capacity can be increased when more videos are uploaded.
- The organisation does not need to maintain all physical storage servers.
- Frequently accessed videos can be delivered from nearby CDN locations.

## Final Evaluation and Design Selection

The HDD-only design is simple but may have higher access latency when many students request videos simultaneously. The HDD and SSD design improves access to popular videos by keeping frequently requested content in faster storage.

Cloud object storage with CDN is suitable when students access videos from many different locations and the platform needs to scale. However, monthly storage and data transfer charges must be considered.

For the proposed system, the HDD and SSD hybrid design is a suitable starting point for a limited budget. Cloud storage with CDN is a better option when the number of students and video requests increases significantly.

## Conclusion

The simulation compares HDD-only storage with an HDD and SSD cache design. The hybrid design is expected to provide faster access to popular videos. Cloud storage with CDN offers another option for supporting students across different locations. The final choice should consider measured performance, storage capacity, network requirements and operating cost.
