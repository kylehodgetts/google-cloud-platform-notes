# Scaling

## Auto-scaling groups of instances

Regional MiG limitations

- Target distribution shape must be EVEN
- To scale in and out, must enable proactive instance redistribution
    - To scale out only, no need

**Target utilization metrics**

Can autoscale based on one or more following metrics

- Average CPU util
- HTTP load balancing serving capacity, which can be based on either util or requests per second
- Cloud monitoring metrics

Can schedule autoscaling for anticipated workloads

Specify Capacity and schedule

# Managed Instance Groups

Much better than creating instances manually

Managed instance groups are better than unmanaged

- Have autoscaling, better than manually adding and removing instances as load changes

Treat resources are ephemeral. Design system to handle instances coming and going.

## Differences between Create Instance and Create Instance Template interface.

- Instance templates - don't need to specify a zone

Instance templates are immutable. Need to copy and create new version

Unmanaged instance groups cannot be multi-zone

- Can add already existing instances to group
- Deleting an unmanaged instance group will leave the instances as it doesn't own them

Managed instance groups

- Can allow and disallow zones where it operates
- Cannot add already existing instances to group, need to specify an instance template
- Deleting a managed instance group will delete the instances because it owns them