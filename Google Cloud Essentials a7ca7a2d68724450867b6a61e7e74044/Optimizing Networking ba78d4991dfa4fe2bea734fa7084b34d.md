# Optimizing Networking

## Connecting through Cloud VPC

- Private network within Google Cloud network infrastructure
- Adds network to Compute Engine, Kubernetes Engine and App Engine (Flex)
- Global resource consisting of regional subnets, connected by WAN
- Includes
    - Firewalls
    - Routes
    - Forwarding Rules
    - Configuration of IP Addresses, external and internal
- Two type of VPC creation
    - Auto mode
    - Custom mode
- Additional services include Shared VPC and Network Peering
    - Shared VPC - share subnets with other projects
    - Network Peering - Private connectivity between VPCs in different projects or organisations

### VPC Lab

Create network

```jsx
gcloud compute networks create $NETWORK_NAME --subnet-mode custom
```

Create subnets

```jsx
gcloud compute networks subnets create $NETWORK_NAME-us-central --network $NETWORK_NAME --region us-central1 --range 10.0.1.0/24
gcloud compute networks subnets create $NETWORK_NAME-eu-west --network $NETWORK_NAME --region europe-west1 --range 10.0.2.0/24
```

List created network

```jsx
gcloud compute networks subnets list --network $NETWORK_NAME
```

Create firewall rule

```jsx
gcloud compute firewall-rules create $RULE_NAME --allow tcp:22,icmp --network $NETWORK_NAME
```

Create instances in network subnet

```jsx
gcloud compute instances create la-vm-us --subnet la-subnet-us-central --zone us-central1-a
gcloud compute instances create la-vm-eu --subnet la-subnet-eu-west --zone europe-west1-b
```

## Optimized Cloud Load Balancing

- Fully managed incoming traffic service
- Distributes traffic across several VM instances
- Benefits:
    - Auto scaling (by policy, CPU util, or serving capacity)
    - Supports heavy traffic
    - Route traffic to closest instances
    - Detect and remove unhealthy instances
- Types of load balancing supported
    - Global external - HTTP/S, SSL, and TCP
    - Regional external - TCP / UDP within a region
    - Regional internal - between groups of instances in a region

## Using Cloud CDN To Deliver

- Accelerates delivery from Compute Engine and Cloud Storage
- Lowers network latency, offload origin servers and reduces serving costs
- Features include:
    - Offers SSL at no extra cost
    - Supports HTTP/1.0, HTTP/1.1, HTTP/2
    - Supports cache invalidation
    - Cache-to-cache filling supported
- General availability caches available to 10 GB, Large Object caching (Beta) to 5TB
- Caching Considerations:
    - Caching is reactive
    - Caches cannot be pre-loaded
    - Once enabled, caching is automatic
    - HTTP(S) load balancer is required

Common scenario - front load LB on cloud storage bucket which get cached by cloud CDN

## Investigating Other Networking Services

### Cloud VPN

- Provides secure connection between on-prem and Cloud VPC
- Utilizes IPSec VPN gateways with encrypted/decrypted traffic
- Features include:
    - Site-to-site VPN via simple topology or with redundancy
    - Supports Internet Key Exchange (IKE) v1 and v2 with shared secret
    - Uses ESP in Tunnel mode with authentication for encryption
- Routing methods supported:
    - Dynamic gateways using Border Gateway Protocol
    - Policy-based routing
    - Route-based VPN
- Best for low - medium traffic: 3 Gbps with direct peering; 1.5 Gbps without (via the public internet)

### Cloud Interconnect

- Provides higher-capacity connections between on-prem and Cloud VPC
- Dedicated Interconnect:
    - Direct physical connections with Google network
    - 69 colocations facilities in 17 regions
    - Highest bandwidth 10 Gbps per circuit (8 circuits max)
    - Routing equipment in colocation facility required
- Partner interconnect
    - Connect to 3rd party service provider
    - Many more connection possibilities
    - Bandwidth from 50 Mbps to 10 Gbps
    - Routing equipment not required
- Public internet bypassed
- VPN tunnels or NAT devices not needed
- Not encrypted - use app level encryption or own VPN