# Gateway Runbook

Gateway provides RESTful and gRPC interfaces to the backend services.
This system is stateless and provides a single interaction point to the ecosystem.

## Failure Mode and Effect Analysis

[FMEA] is a method of failure analysis that helps teams create reliable systems and develop comprehensive on-call response patterns.

[FMEA]: https://en.wikipedia.org/wiki/Failure_mode_and_effects_analysis

| Service   | Failure Mode         | Possible Cause       | Effects                           | Probability (P)        | Severity (S)    | Detection (D) | Risk      |
|:----------|:---------------------|:---------------------|:----------------------------------|:-----------------------|:----------------|:--------------|:----------|
| DockerHub | Outage / Unreachable | DockerHub DDOSd      | Cannot update or deploy gateway   | remote (B)             | no effect (I)   | high          | low       |
| Gateway   | Not Running / Ready  | Crash loop           | Unable to serve user requests     | extremely unlikely (A) | critical (IV)   | certain       | low       |
| Gateway   | Not Running / Ready  | Cluster full         | Unable to serve user requests     | remote (B)             | critical (IV)   | high          | moderate  |
| Gateway   | Not Running / Ready  | Unhealthy dependency | Unable to serve user requests     | remote (B)             | critical (IV)   | high          | moderate  |

### Production Outage Scenarios

- [Gateway not ready](gateway-notready.md)

<!--
## Dashboards

Links to the Dashboards for this service

## Alerts
Links to the Alerts for this service

For Every Alert there should be a corresponding section in alphabetical order
### Alert Title
Alert Description:  Why do we have this alert?  What does it mean?  What is typically the cause of this alert?

#### Impact to Customers:
How does this situation impact our customers?  If the customers are not being impacted, this is a good indicator that the alert can be deleted.

#### Remediation Steps:
Checklist manifesto style steps for how to resolve this alert.  A person who has never worked on our stack should be able to follow these steps and remediate the incident.  If it cannot be remediated, include escalation steps here.
 1. Do this
 2. Check this graph
 3. Do this thing 
 4. Do this other thing
 5. Verify service has recovered

## Deployment
How do you deploy this services.  Favor Checklist manifesto style lists here as well. 
 1. Do this thing
 2. Do this other thing
 3. Finally do this thing 
 
### Canary Deploy
Instructions on how to do a Canary Deployment
 1. Do this canary thing
 2. another canary task
 
### Rollback Deploy
Instructions on how to Rollback a Deploy. 
 1. Get the rollback build here
 2. Do this thing
 3. Do this other thing.  
-->
