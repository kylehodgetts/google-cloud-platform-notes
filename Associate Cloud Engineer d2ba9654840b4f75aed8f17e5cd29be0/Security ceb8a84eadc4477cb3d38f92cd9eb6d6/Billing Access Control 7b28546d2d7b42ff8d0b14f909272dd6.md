# Billing Access Control

## Billing Accounts

- represents some way to pay for GCP service usage
- Type of resource that belongs to org but lives outside of projects
    - Inherits org-level IAM policies
- Can be linked to projects
    - but does not own them
        - No impact on project IAM

![Billing%20Access%20Control%207b28546d2d7b42ff8d0b14f909272dd6/Screenshot_2021-08-03_at_12.27.40.png](Billing%20Access%20Control%207b28546d2d7b42ff8d0b14f909272dd6/Screenshot_2021-08-03_at_12.27.40.png)

## Billing Account User

Role: Billing Account User

Purpose: Link projects to billing accounts

Level: Org or billing account

Use Case: 

- Very restricted permisions, can grant it broadly
    - Typically in combo with Project Creator
        - Allows user to create new projects linked to the billing account in which the role is granted

## Billing IAM Roles

[Roles](Billing%20Access%20Control%207b28546d2d7b42ff8d0b14f909272dd6/Roles%2043a9ea89ee2544a0885abd9efef24d55.csv)

## Monthly Invoiced Billing

- Get billed monthly and pay by invoice due date
- Can pay via check or wire transfer
- Can increase project and quota limit
- Billing admin or orgs current billing account contacts Cloud Billing Support
    - Determine eligibility
    - Apply to switch to monthly invoicing
- Eligibility depends on:
    - Account age
    - Typical monthly spend
    - Country

## SMB Centralized

Scenario: Small-to-medium enterprise with preference for centralized control

**User Type - Billing Activities - Billing Cloud IAM Roles**

CEO

- Billing Activities
    - Manage payment instrument
    - View and approve invoices
- IAM Roles
    - Billing Account Administrator

CTO

- Billing Activities
    - Set budget alerts
    - View spend
    - Create new billable projects
- IAM Roles
    - Billing Account Administrator
    - Project Creator

Development teams

- Billing Activities
    - None
- IAM Roles
    - None

## SMB Delegated

Scenario: Small-to-medium enterprise with preference for centralized control

CEO

- Billing Activities
    - Manage payment instrument
    - Delegate Authority
- IAM Roles
    - Billing Account Administrator

CFO

- Billing Activities
    - Set budget alerts
    - View spend
- IAM Roles
    - Billing Account Administrator

Accounts Payable

- Billing Activities
    - View and approve invoices
- IAM Roles
    - Billing Account Viewer

Development teams

- Billing Activities
    - Create new billable projects
- IAM Roles
    - Billing Account User
    - Project Creator