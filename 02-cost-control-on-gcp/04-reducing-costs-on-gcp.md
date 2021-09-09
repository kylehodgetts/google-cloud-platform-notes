# Reducing Costs on GCP

High level overview of cost reduction tools available on GCP

- Rightsize VMs
- Sustained Use Discounts
- Committed use discounts
- Preemptive vms
- Cloud storage classes and lifecycle policies
- Free Tier products

## Rightsizing VMs

Why?

- Paying for more compute than needed is a waste of money
- Scope machine type to match resource usage (up or down)

How?

- GCP recommends sizing based on metrics from previous 8 days
- Recommends resizing machine type up or down to fit actual usage
- Properly sized machine = more efficient usage = money saved
- Automatically generated
- Resizing machine requires restart

## Sustained Use Discounts

Automatic

Long running compute CPU or RAM automatically discounted

How?

- When a set of amount of compute is used for at least 25% of the month, discount is applied
- Compute does not need to be used on the same instance
- Calculations for sustained usage across all mix and match scenarios automatically applied
- Discounts uptown 30% of costs
- Note: does not overlap with **committed use discounts**

## Committed Use Discounts

Commit to a set of amount of compute = save $$$

Save up to 70%

How?

- 1 or 3 year commitments
- Purchase set amount of compute or GPU or local SSDs at a discount
- Billed monthly, but billed regardless of use (or non use) of resources
- E.g. 1 year committed use contract for 8 CPUs and 32GB of RAM
    - Can be used in single instance of spread across multiple
    - Delete one instance and create another using same specs
- Committed use resources are not eligible for sustained use discount
    - Resources above committed are eligible

## Preemptive VMs

Short-lived, low cost VMs at huge discounts: up to 80%

How?

- Most instances have option for preemptive VMs
- Can be shut down at any time if capacity is needed
- Max life of 24 hours regardless
- Not ideal for critical servers
- Ideal for fault-tolerant batch computing workloads
    - "Throw a bunch of cheap, disposable VMs at a problem"

## Cloud Storage Classes

Object-level availability based on access needs

How?

- Default storage class has no restrictions on availability, modification or retrieval access but highest costs
    - Hot data
- Lower price classes restrict how often data can be modified or retrieved without an additional fee
    - Ideal for infrequently accessed data (backups, archive data)
- Classes
    - Standard
    - Nearline
    - Coldline
    - Archive
- Cheaper the class = longer data needs to sit before modifying it without a fee
- Retrieving data also incurs a fee
    - Higher with cheaper storage classes

## Cloud Storage Lifecycle Policies

Automatically delete or change class of old data

How?

- Old data that is no longer frequently accessed shouldn't remain in standard class (or exist at all)
- Solution: automatically delete or change class based on age or other factors
- Don't need to do it manually as lifecycle policies do it for you

## Free Tier products

Always free, never expires

What?

- Low usage of many GCP services is always free
- Usage above free tier amounts is charged normally
- Great for low usage of services for testing or low traffic workloads
- Examples
    - 1 free f1-micro GCE instance per month
    - 5 GB of cloud storage space used per month
    - 1TB of BigQuery queries per month