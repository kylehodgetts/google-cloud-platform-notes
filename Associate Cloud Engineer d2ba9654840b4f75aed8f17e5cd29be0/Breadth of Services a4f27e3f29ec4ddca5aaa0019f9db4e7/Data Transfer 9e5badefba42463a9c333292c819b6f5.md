# Data Transfer

## Data Transfer Appliance

[Overview | Transfer Appliance | Google Cloud](https://cloud.google.com/transfer-appliance/docs/4.0/overview)

- Rackable, high-capacity storage server to physically ship data to Google Cloud Storage
    - AWS snowball
- 100 TB or 480 TB versions
- 480 TB a week is faster than saturated 6 Gbps link

## Storage Transfer Service

[Storage Transfer Service | Google Cloud](https://cloud.google.com/storage-transfer-service)

- Global
- Copies objects for you, don't need to set up machine to do it
- Destination is always GCS bucket
- Source can be S3, HTTP(S) endpoint or another GCS bucket
- One-time or scheduled recurring transfers
- Free to use but pay for its actions