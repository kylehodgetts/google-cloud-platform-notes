# Operations and Management

## Stackdriver

[Operations: Cloud Monitoring & Logging | Google Cloud](https://cloud.google.com/products/operations)

- Global
- Family of services for monitoring, logging and diagnosing apps on GCP, AWS or Hybrid
- Service integrations add lots of value - among Stackdriver and with GCP
- One Stackdriver account can track multiple:
    - GCP projets
    - AWS accounts
    - Other resources
- Simple usage based pricing
    - No longer previous system of tiers, allotments and overages

## Stackdriver Monitoring

[Cloud Monitoring | Google Cloud](https://cloud.google.com/monitoring/)

- Global
- Visibility into perf, uptime & overall health of cloud apps (based on collectd)
- Includes built-in, custom metrics, dashboards, global uptime monitoring and alerts
- Follow the trail: Links from alerts to dashboards and charts to logs to traces
- Cross-cloud: GCP, but monitoring agent also supports AWS
- Alerting policy config includes multi-condition rules & resource organisation
- Alert via email, GCP mobile app, SMS, Slack, PagerDuty, AWS SNS, webhook etc
- Automatic GCP/Anthos metrics always free
- Pay per API calls and per MB for custom or AWS metrics

## Stackdriver Logging

[Cloud Logging | Google Cloud](https://cloud.google.com/logging/)

- Global
- Store, search, analyse, monitor and alert on log data and events (Fluentd)
- Collection built into some GCP, AWS support with agent or custom send via API
- Debug issues with integration with Stackdriver Monitoring, Trace & Error Reporting
- Create real-time metrics from log data, then alert or chart them on dashboard
- Send real-time log data to BigQuery for advanced analytics and SQL like querying
- Power interface to browse, search and slice log data
- Export log data to GCS to cost-effectively store log archives
- Pay per GB ingested & stored for one month but first 50GB per project is free
- Cloud Audit Logging / Access Transparency logs also free

## Stackdriver Error Reporting

[Error Reporting | Google Cloud](https://cloud.google.com/error-reporting/)

- Global
- Counts, analyses, aggregates and tracks crashes in helpful centralised interface
- Smartly aggregates errors into meaningful groups tailored to language / framework
- Instantly alerts when a new app error cannot be grouped with existing ones
- Link directly from notifications to error details:
    - Time chart
    - occurrences
    - Affected user count
    - first and last seen dates
    - Cleaned stack
- Exception stack trace parser knows Java, Python, JS, Ruby, C#, PHP and Go
- Jump from stack frames to source to start debugging
- No direct charge, pay for source data in Stackdriver Logging

## Stackdriver Trace

[](https://cloud.google.com/trace/)

- Global
- Tracks and displays call tree & timings across distributed systems to debug performance
- auto captures traces from Google App Engine
- Trace API and SDKs for Java, Node, Ruby, Go capture traces from anywhere
- Zipkin collector allows Zipkin tracers to submit data to Stackdriver Trace
- View aggregate app latency info or dig into individual traces to debug problems
- Generate reports on demand and get daily auto reports per traced app
- Detects app latency shift (degradation) over time by evaluating perf reports
- Pay for ingesting and retrieving trace spans

## Stackdriver Debugger

[Cloud Debugger | Google Cloud](https://cloud.google.com/debugger/)

- Global
- Grab program state (callstack, variables, expressions) in live deploys; low impact
- Logpoints repeat for up to 24h; fuller snapshots run once but can be conditional
- Source view supports Cloud Source Repository, Github, Bitbucket, local and upload
- Java and Python supported on GCE, GKE, and GAE (Standard and Flex)
- Node and Ruby supported on GCE, GKE and GAE Flex.
- Go only on GCE and GKE
- Auto enabled for GAE apps; agents available for others
- Share debugging sessions with others (via URL)
- Free

## Stackdriver Profiler

[Cloud Profiler | Google Cloud](https://cloud.google.com/profiler/)

- Global
- Continuous CPU and memory profiling to improve perf and reduce cost
- Low overhead (Typical: 0.5%; Max 5%) so use it in prod too
- Supports: Go, Java, Node and Python 3.2+
- Agent based
- Saves profiles for 30 days
- Can download profiles for longer term storage
- Free

## Cloud Deployment Manager

[Google Cloud Deployment Manager documentation](https://cloud.google.com/deployment-manager/docs)

- Global
- Create and manage resources using declarative templates "IaC"
- Declarative allows automatic parallelization
- Templates written in YAML, Python or Jinja2
- Supports input and output parameters with JSON Schema
- Create and update of deployments both support preview
- Free; pay for resources involved in deployments

## Cloud Billing API

[Cloud Billing documentation | Google Cloud](https://cloud.google.com/billing/docs/)

- Global
- Programmatically manage billing for GCP projects and get GCP pricing
- Billing config
    - List billing accounts, get details and associated projects for each
    - Enable (associate), disable (disassociate), or change project's billing account
- Pricing
    - List billable SKUs; get public pricing (including tiers) for each
    - Get SKU metadata like regional availability
- Export of current bill to GCS or BQ is possible - but configured via console, not API