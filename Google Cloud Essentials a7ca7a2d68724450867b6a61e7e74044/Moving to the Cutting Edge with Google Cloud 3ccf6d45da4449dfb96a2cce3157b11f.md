# Moving to the Cutting Edge with Google Cloud

## Machine Learning with Cloud AI

- Collection of services and APIs designed to facilitate machine learning
- Includes hardware accelerators: TPUs (TensorFlow Processing Units)
- Primary service: Cloud Machine Learning Engine (ML Engine)
    - Training
        - Trains computer models to recognize patterns in data
        - Supports TensorFlow, scikit-learn and XGBoost
    - Prediction
        - Online
            - Real-time processing with fully managed ML Engines
            - No Docker container required & supports multiple frameworks
        - Batch
            - For async operations
            - Scales to terabytes of data
- Data must be stored in accessible location e.g. Cloud Storage

## Real World Integration via Cloud IoT

- Fully managed service for connecting and managing IoT devices
- Devices must be registered
- Works with both telemetry (event data) & device state data
- Receives data and sends to Cloud Pub Sub Topic
- Supports HTTP and MQTT (Message Queue Telemetry Transport) protocols for communication
- Highly secure:
    - Each device uses JSON Web Tokens for public / private keys
    - Supports RDS or Elliptic Curve algorithms to verify signatures
    - Key rotation support
    - Access to IoT core controlled by Cloud IAM roles and permissions
- Part of an IoT eco-system with Android Things and Google Beacon

## Migrating Info through Data Transfer

- Range of options available for transferring data to Google Cloud
- **Online Transfer**
    - Tools available: Console upload, JSON REST API, gsutil

- **Storage Transfer Service**
    - Imports online data to Cloud Storage
    - Supports transfer of objects from AWS S3
    - Select source bucket
        - Google cloud storage bucket
        - S3 bucket
        - List of object URLs
    - Can set filters on files to transfer
    - Select destination bucket in Cloud Storage
    - Configure transfer
        - Run now
        - Run daily at a specified time

- **Transfer Appliance**
    - Physical device loaded on-prem and shipped to Google data center
    - Single device can hold petabyte of data
    - Far faster than online transfer for large amounts of data