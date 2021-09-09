# Internal Networking

## Virtual Private Cloud (VPC)

[Virtual Private Cloud (VPC) | Google Cloud](https://cloud.google.com/vpc/)

- Global, Regional
- Global IPv4 unicast software defined network for GCP resources
- Automatic mode; custom mode gives control
- Configure subnets, routes, firewall, VPNs, BGPs etc
- VPC is global and subnets are regional
- Can be shared across multiple projects and peered with other VPCs
- Can enable private (internal IP) access to some GCP services e.g. BQ, GCS)
- Free to configure VPC
- Pay to use services (e.g. VPN) and for network egress

## Cloud Interconnect

[Cloud Hybrid Connectivity - Faster Networking | Network Connectivity](https://cloud.google.com/hybrid-connectivity)

- Regional, multi-regional
- Options for connecting external networks to Google's network
- Private connections to VPC via Cloud VPN or dedicated / partner interconnect
- Public Google services (inc GCP) accessible via External peering (No SLAs)
    - Direct peering for high volume
    - Carrier peering via a partner for lower volume
- Significantly lower egress fees
    - Except Cloud VPN which remains unchanged

## Cloud VPN

[Cloud VPN overview | Google Cloud](https://cloud.google.com/network-connectivity/docs/vpn/concepts/overview)

- Regional
- For persistent static connections between gateways (i.e. not for a dynamic client)
    - Peer VPN gateway must have static IP
- Encrypted link to VPC (as opposed to Dedicated Interconnect) into one subnet
- Supports both static and dynamic routing
- 99.9% availability SLA
- Pay per tunnel-hour
- Normal traffic charges apply

## Dedicated Interconnect

[Dedicated Interconnect overview | Google Cloud](https://cloud.google.com/network-connectivity/docs/interconnect/concepts/dedicated-overview)

- Regional, Multi-Regional
- VLAN attachment is private connection to VPC in one region
    - No public GCP APIs
    - Region chosen from those supported by particular Interconnect location
- Links are private but not encrypted
    - Can layer your own encryption
- Redundant connection in different locations recommended for critical apps
    - Redundancy achieves 99.99% availability; otherwise 99.9% SLA
- Pay fee per 10 Gbps link plus (relatively small) fee per VLAN attachment
- Pay reduced egress rates from VPC through Dedicated Interconnect

## Cloud Router

[Cloud Router documentation | Google Cloud](https://cloud.google.com/network-connectivity/docs/router)

- Regional
- Dynamic routing (Border Gateway Protocol BGP) for hybrid networks linking GCP VPCs to External Networks
- Works with Cloud VPN and Dedicated Interconnect
- Automatically learns subnets in VPC and announces them to on-prem network
- Without cloud router, must manage static routes for VPN
    - Changing IP addresses on either side of VPN requires recreating it
- Free to set up
- Pay for usual VPC egress

## CDN Interconnect

[CDN Interconnect overview | Google Cloud](https://cloud.google.com/network-connectivity/docs/cdn-interconnect)

- Regional, Multi-Regional
- Direct, low latency connectivity to certain **external** CDN providers with cheaper egress
    - Akamai, Cloudflare, Fastly, and more
- Works for both pull and push cache fills
    - Because its for all traffic with that CDN
- Contact CDN provider to set up for GCP project and which regions
- Free to enable, then pay less for the egress you configured