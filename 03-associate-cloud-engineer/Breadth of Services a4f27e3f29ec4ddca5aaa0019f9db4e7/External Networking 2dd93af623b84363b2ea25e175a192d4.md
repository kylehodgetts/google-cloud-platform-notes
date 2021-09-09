# External Networking

## Google Domains

[https://domains.google/#/](https://domains.google/#/)

- Global
- Google's registrar for domain names
- Private Whois records
- Built-in DNS or custom nameservers
- Supports DNSSEC
- Email forwarding with automaic setup of SPF and DKIM (for built-in DNS)

## Cloud DNS

[](https://cloud.google.com/dns/)

- Global
- Scalable, reliable & managed authoritative DNS service
- 100% uptime guarantee
- Public and private managed zones
    - Allows for split horizon DNS - maps to different addresses depending on whether queried internally or externally
- Low latency globally
- Supports DNSSEC
- Manage via UI, CLI or API
- Pay fixed fee per manged zone to store and distribute DNS records
- Pay for DNS lookups (usage)

## Static IP

[Reserving a static external IP address | Compute Engine Documentation](https://cloud.google.com/compute/docs/ip-addresses/reserve-static-external-ip-address)

- Regional or Global
- Reserve static IP addresses in projects and assign them to resources
- Regional IPs used for GCE instances & Network Load Balancers
- Global IPs used for global load balancers
    - HTTP(S), SSL proxy, TCP proxy
    - Anycast IP simplified DNS
- Pay for reserved IPs that are not in use

## Cloud Load Balancing

[Cloud Load Balancing | Google Cloud](https://cloud.google.com/load-balancing/)

- Regional or Global
- High-perf, scalable traffic distribution integrated with autoscaling & Cloud CDN
- SDN naturally handles spikes without prewarming; no instances or devices
- Regional NLB: health checks, round robin, session affinity (send requests from a user to same instance for a while)
    - Forwarding rules set up based on IP, protocol (TCP, UDP) and (optionally) port
- Global Load Balancers with multi-region failover for HTTP(S), SSL proxy & TCP proxy
    - Prioritize low-latency connection to region closest to user then gently failover in bits
    - Reacts quickly (unlike DNS) to changes in users, traffic, network, health etc
- Pay by making ingress traffic billable (cheaper than egress) plus hourly per rule

## Cloud CDN

[Cloud CDN: Content Delivery Network | Google Cloud](https://cloud.google.com/cdn/)

- Global
- Low latency content delivery based on HTTP(S) CLB & integrated with GCE and GCS
- Supports HTTP/2 and HTTPS, bu no custom origins (GCP only)
- Simple checkbox on HTTP(S) Load Balancer config turns this on (HTTPS)
- On cache miss, pay origin → POP (point of presence) "cache fill" egress charge (cheaper for in-region)
- Always pay POP → client egress charges, depending on location
- Pay for HTTP(S) request volume
- Pay per cache invalidation request (not per resource invalidated)
- Origin costs (e.g. CLB, GCS) can be much lower because cache hits reduce load