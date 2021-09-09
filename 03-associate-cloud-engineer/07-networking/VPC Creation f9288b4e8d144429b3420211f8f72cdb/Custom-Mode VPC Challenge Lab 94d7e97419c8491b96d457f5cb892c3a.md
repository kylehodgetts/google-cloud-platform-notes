# Custom-Mode VPC Challenge Lab

Desired Result

- Two-tier setup: Frontend and Backend, each autoscaled across 2+ zones
- Use ICMP (ping) to represent flow of traffic
    - Real world usage would use other ports and protocols like TCP 80, 443, 3306
- Frontend
    - Accepts incoming from internet
    - Can connect outbound to backend and internet
- Backend
    - Only accepts incoming from frontend or other backend
    - No outbound anywhere

Add 'implied' ingress and egress rules with HIGH priorities

- Implied block all ingress
- Implied allow all egress