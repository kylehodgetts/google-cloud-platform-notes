# Storage

## Local SSD

[Storage options | Compute Engine Documentation | Google Cloud](https://cloud.google.com/compute/docs/disks/#localssds)

- Zonal
- Very fast 375GB SSD on the physical servers
- Can stripe across 8 for even better performance
- Data will be lost when instance shuts down
    - Can survive a live migration
- Data encrypted at rest
- Pay for GB a month

## Persistent Disk (PD)

[Persistent Disk: durable block storage | Google Cloud](https://cloud.google.com/persistent-disk/)

- Zonal
- Flexible block based network attached storage
- Boot disk for every GCE instance
- Data encrypted between instance and storage
- Faster the larger they are
- Persist and replicate for durability
- Can resize while in use upto 64GB
    - Need to resize file system within VM
- Snapshots (and machine images), add even more capability and flexibility
    - Incremental - only pay for incremental $ and time
    - Use like full backup
- Not file base NAS
- Can mount to multiple instances if all are **read-only**
    - Cannot update it while in use in this case
- Pay for GB a month provisioned based on perf class
    - Plus snapshot GB a month used

## Cloud Filestore

[Filestore: Fully managed cloud file storage | Google Cloud](https://cloud.google.com/filestore/)

- Zonal
- Full managed file based storage
    - as opposed to block based
- Predictably fast performance for file based workloads
- Accessible to GCE and GKE through VPC, via NFSv3 protocol
- Primary use case is application migration to cloud (lift and shift)
- Fully manages file serving but not backups
- Pay for provisioned TBs in Standard or Premuim tier
    - Min provisioned capacity of 1TB (standard) or 2.5TB (premium)

## Cloud Storage (GCS)

[Cloud Storage | Google Cloud](https://cloud.google.com/storage/)

- Regional or Multi-regional
- Scalable, fully managed, versioned and highly durable object storage
- Designed for 11-nines durability
- Strongly consistent
    - Even for overwrite PUTs and DELETEs
- Integrated site hosting and CDN functionality
- Lifecycle transitions across classes
    - Multi-Regional
        - Data needs to be spread out for whatever reason
    - Regional
        - Faster access in particular location
    - Nearline
        - Access data less than once a month
    - Coldline
        - Access data less than once a year
- Diffs in cost and availability, not latency
- All class have same API, can use gsutil and gcsfuse to mount them as file system
- Pay for data operations and GB months stored by class
- Nearline and Coldline: also pay for GB retrieved - plus early deletion fee if < 30 or 90 days