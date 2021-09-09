# Intro to GCP

# Design Principles

## Global

- Serve worldwide customers
- Regional model
    - simplifies data sovereignty
- Secure
- Huge scale
- for developers

## Physical Infra

- vCPU
- Physical Server
- Rack
- Data Center
- Zone
    - one or more data centers
    - Independent from other zones
- Region
    - One or more zones
    - Quick inter zone communication
- Multi-region
- Regions and zones connected by private global network
- Points of Presence (POPs) - network edges and CDN locations

## Network Ingress and Egress

Google: route so traffic enters from Internet at edge closest to source

Can now opt for normal networking routing to reduce price (and functionality)

## Pricing

- Provisioned - Make sure you're ready to handle X
- Usage - Handle whatever I use and charge me for it
- Network traffic
    - Free on ingress
    - Charges on Egress by GBs used
    - Egress to GCP services is sometimes free
        - Depends on location of service

## Security

- Separation of duties and physical security
- Everything encrypted at rest
- String key and identity management
- Network encryption
    - All control info is encrypted
    - All WAN traffic to be encrypted automaticall
    - Moving towards encrypting all local traffic within data centers
- Distrust the network - by default
    - BeyondCorp

## Scale and Automation

Scalability must be unbounded

## Resource Quota (soft limits)

How much of a service you're allowed to use

- Scope
    - Regional
    - Global
- Changes
    - Automatic
    - By Request
        - Response in 24-48h
        - May be refused
- Queryable
    - `gcloud compute project-info describe —project myprojectid`

 

## Organization

- Project is similar to AWS account
- Projects own resources
    - Can share resources with other projects
- Projects can be grouped and controlled in a hierarchy