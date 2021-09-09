# Development and APIs

## Cloud Source Repositories

[Cloud Source Repositories | Google Cloud](https://cloud.google.com/source-repositories/)

- Global
- Hosted private git repos with integrations to GCP and other hosted repos
- Supports standard git functionality
- no enhanced workflow support like PRs
- Can setup auto sync from github or bitbucket
- Natural integration with Stackdriver debugger for live-debugging deployed apps
- Pay per project user active each month (not prorated)
- Pay per GB-month of data stored (prorated)
- Pay per GB of data egress

## Cloud Build

[Cloud Build Serverless CI/CD Platform | Google Cloud](https://cloud.google.com/build)

- Global
- Continuously takes source code and builds, tests and deploys it for you - CI/CD service
- Trigger from Source Repo by branch, tag or commit or ZIP in GCS
    - Can trigger from Github and bitbucket via RepoSync
- Run many builds at once (10 at a time)
- Dockerfile: Simple build + push - plus scans for package vulnerabilities
- JSON/YAML file: flexible & parallel steps
- Push to GCR & export artifacts to GCS or anywhere your build steps write
- Maintains build logs and history
- Pay per minute of build time but free tier is free 120 mins a day

## Container Registry

[Container Registry | Google Cloud](https://cloud.google.com/container-registry/)

- Regional, Multi-Regional
- Fast, private ocker image storage based on GCS with Docker V2 registry API
- Creates and manages multi-regional GCS bucket then translates GCR calls to GCS
- IAM integration simplifies builds and deployments within GCP
- Quick deploy because of GCP networking to GCS
- Directly compatible with standard Docker CLI: Native Docker Login support
- UX integrated with Cloud Build and Stackdriver logs
- UI to manage tags and search for images
- Pay directly for storage and egress of underlying GCS (no overhead costs)

## Cloud Endpoints

[Cloud Endpoints | Google Cloud](https://cloud.google.com/endpoints/)

[Architectural overview of Cloud Endpoints](https://cloud.google.com/endpoints/docs/openapi/architecture-overview)

[Transcoding HTTP/JSON to gRPC | Cloud Endpoints with gRPC](https://cloud.google.com/endpoints/docs/grpc/transcoding)

- Global
- Handles AuthN, monitoring, logging & API keys for APIs backed by GCP
- Based on Nginx
- Proxy instance are distributed and hook into CLB
- Fast Extensible Service Proxy (ESP) container based on Nginx: < 1ms a call
- Uses JWT and integrates with Firebase, Auth0, & google Auth
- Integrates with Stackdriver Logging and Stackdriver Trace
- ESP can transcode HTTP/JSON to gRPC
    - API needs to be resource oriented (RESTful) for this to work
- Pay per call to your API

![Screenshot 2021-09-09 at 21.47.38.png](Development%20and%20APIs%200ee76017fc284e20b628b876ce5fc0c7/Screenshot_2021-09-09_at_21.47.38.png)

## Apigee

[Apigee API Management | Google Cloud](https://cloud.google.com/apigee)

- Global
- API management platform for whole API lifecycle
- Transforms calls between protocols: SOAP, REST, XML, Binary etc
- Authenticate via OAuth, SAML, LDAP, Authorize via RBAC
- Throttle traffic with quotas, manage API versions etc
- Apigee Sense identifies and alerts admins to suspicious API behaviors
- Apigee API Monetization supports various revenue models / rate pans
- Team and Business tiers are flat monthly rate with API call quotas & feature sets
- "Enterprise" tier and special feature pricing are "Contact Sales"

## Test Lab for Android

[Firebase Test Lab](https://firebase.google.com/docs/test-lab/)

- Cloud Infra for running test matrix across variety of real Android devices
- Production grade devices flashed with Android version and locale you specify
- Robo test captures log files, saves annotated screenshots & video to show steps
    - Default completely automatic but still deterministic so can show regressions
    - Can record custom script
- can also run Espresso and UI automator 2.0 instrumentation tests
- Firebase Spark and Flame plans have daily allotment of physical and virtual tests
- Blaze (Pay as you go) plan charges per device-hour - much less for virtual devices