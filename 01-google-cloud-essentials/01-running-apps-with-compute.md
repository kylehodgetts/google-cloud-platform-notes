# Running Apps with Compute

## Rapid Development via App Engine

Infinite scale - globally

PaaS

- highest managed compute service in lineup

No server setup and minimal management overhead

- Less you're able to configure

Auto scaling to virtual instances and auto load balancing

Great for websites and mobile apps and business apps that need to get up and running quickly

Standard Environment

- Propriety
    - Use specific google APIs
- Limited language support
- Fasted spin up time of cloud compute. In ms
- Less expensive

Flexible Environment

- More recent
- Less proprietary
- Standardized on Docker
- Broader language and version use
- Slower instance spin up
- More expensive

## Running Virtual Machines with Compute Engine

More flexible than app engine.

- IaaS - Infra as a service
- Scalable high-performance VMs
- Numerous configs, completely customizable
- Run public disk images or private images
    - Think: Amazon AMIs
- Various storage options
- Optionally, works with containers
- VPC Support
- Default and custom firewalls
- Complete routing support

Zonal resource

- Pick zone closest to target market

### Instance Groups

Managed

- Group of identical instances
- manage as a single unit
- Autoscale, LB, health problems will be dealt with
    - Auto recreate bad instances
- Can be zonal or regional
    - Can have instances in multiple zones if regional

Instance templates

- Use templates to spin up identical instances
- Global resource —> can be assigned to any region or zone

Unmanaged

- Collections of instances with different configs
    - Used when needed Load balancing to existing instances
- Better to go with managed

### Disks

Standard HD persistent disks

SSD Persistent disks

Placed remotely from server

Use local SSD Persistent disk for low latency

### TPUs

Tensor processing units

Computing hardware used to accelerate machine learning workloads

## Standardizing on Kubernetes

- Managed, orchestrated environment for containerized applications
- Uses Compute Engine Instances to form cluster
- Replies on Open Source Kubernetes Cluster management system
- Currently only Docker containers are supported
- Benefits
    - Load-balancing integrated
    - Node pools supported
    - Automatic cluster and node scaling
    - Automatic upgrades
    - Automatic repair based on health reports
    - Automatic logging and monitoring with StackDriver

## Specializing with Cloud Functions

- Serverless environment for executing code and connecting cloud services
- Fully managed: zero infra or management requirements
    - Scales really fast
- Javascript functions in a Node.js wrapper
- Triggers
    - HTTP request
    - Cloud storage event
    - Pub sub event
        - `gcloud pubsub topics publish $TOPIC_NAME --message "y'all"`
- Use cases
    - Webhooks - Respond to any HTTP event
    - Data and image processing - validate and transform data or manipulate images
    - Mobile backend - react to storage, authentication or data events
    - IoT - Respond to pub sub messages from devices

Call function from command line

```jsx
DATA=$(printf 'my friends' | base64)
gcloud functions call $FUNCTION_NAME --data '{"data":"'$DATA'"}'
```