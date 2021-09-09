# App Engine

No servers to maintain

Upload app and go

Features supported natively and highly customizable:

- Automatically scales based on incoming traffic
- Load balancing
- Microservices
- Auth
- SQL and NoSQL databases
- Traffic splitting
- logging
- search
- versioning
- roll out and roll backs
- security scanning

App engines Flexible environment supports host of programming languages

- Java
- Python
- PHP
- NodeJS
- Ruby
- Go

[Choosing an App Engine environment | App Engine Documentation](https://cloud.google.com/appengine/docs/the-appengine-environments)

## Standard env vs Flexible env

### Standard env

Runs in sandbox using runtime of language

Choose standard env

- Source code written in very specific versions of supported programming languages
- Intended to run for free or at low cost
    - Pay for only whats needed
- Experiences sudden and extreme spikes of traffic which require immediate scaling

### Flexible env

Runs in Docker Containers on Compute Engine VMs

Choose flexible env:

- Application receives consistent traffic
- Experience regular traffic fluctuations
- Meet parameters for scaling up and down gradually
- Application runs in docker container
- uses or depends on frameworks that include native code
- Accesses the resources or services of your Google Cloud project that reside in the Compute Engine network
- Don't plan to go below 1 instance

## Lab

Lab environment

- One Codeloab
- One qwiklab

Choose deployment

- Non-container lab
- One container lab