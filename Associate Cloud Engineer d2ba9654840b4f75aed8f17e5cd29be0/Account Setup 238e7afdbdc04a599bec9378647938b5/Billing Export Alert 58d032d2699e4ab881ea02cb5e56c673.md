# Billing Export / Alert

## Billing Export

- Export must be setup per billing account
- Resources should be placed into appropriate project
- Resources should be tagged with labels
- Billing export is not real time
    - Delay in hours

Create data set in BigQuery `billing_export`

Go to Billing > Billing export

Under daily cost detail, edit settings.

Select the project that contains the data set and then select the data set id

## Billing Alert

To notify billing admins when spend exceeds % of budget