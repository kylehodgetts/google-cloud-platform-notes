# Cost Visibility and Analysis

- Gain a detailed view of costs with billing exports
- Export billing data to BigQuery for further analysis
- Set budges and alerts to avoid unplanned suprises

## Cost Visibility with Billing Reports

Why?

### Visibility into all costs

- We cannot reduce costs if we don't now what we're paying to begin with

Billing reports answer these questions

- how much is the spend in the cloud
- Cost trends - predicted
- What is driving costs
    - Product, project, SKU etc

## Exporting Billing Data to BigQuery

Export to cloud storage is deprecated

Recommendation is to export to BigQuery only.

Why?

- Perform further in-depth analytics of billing data
    - Pair BQ with data analytics tools

How?

Create a big query data set in advance

- Requires **BigQuery user** role in export project

Configure billing export to the above dataset

- Requires a **Billing Account Administrator** role

Will only capture new data generated after export is created.

## Billing Alerts with Budgets

Why?

- Avoid surprises on bill
    - Alerted of runaway costs before they get out of hand

Scenario

- monthly spend is $500 a month
- Bob wants to explore Cloud Spanner service
    - Creates multi region instance but forgets to delete it
    - Costs $6000 a month!
- Need to know about this cost anomaly
- Set the budget to $600
- Receive notifications of budget threshold, alerting use to anomalies for further investigation
- Result - Alerted of surprise expenses before they become a big suprise

How?

- Create a budget
    - Set the scope to entire account or limit by project ID, product, label
- Set alert thresholds
    - Configure alerts for reaching different percentages of monthly budget
- Configure notifications based on threshold reached
    - By default, all billing admins are notified
    - By default, no resources are disabled after meeting budget limit
        - Can set up pub sub topics and subscriptions to take automated action
        - Send notifications to Cloud monitoring