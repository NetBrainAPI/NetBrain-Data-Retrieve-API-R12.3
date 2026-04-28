# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Key Fields Evaluated](#key-fields-evaluated)
- [Evaluation Logic](#evaluation-logic)
- [Interpretation](#interpretation)
- [Success Criteria](#success-criteria)
- [Alert Criteria](#alert-criteria)
- [Use Case Examples](#use-case-examples)
- [Reference](#reference)


# Overview <a name="overview"></a>
The <b>Deployment Health</b> API monitors the health status of Kubernetes deployments by comparing the desired number of replicas with the actual and ready replicas.

A deployment is considered healthy when the number of available or ready pods matches the desired replica count. Any mismatch may indicate issues such as:

* Failed pod scheduling
* Image pull errors
* CrashLoopBackOff
* Resource constraints
* Ongoing or failed rollouts

This API retrieves deployment status directly from the Kubernetes API server.


# Metric Info <a name="metric-info"></a>
* <b>Resource Type</b>: Deployment (apps/v1)
* <b>Source</b>: Kubernetes API Server
* <b>Endpoint</b>: /apis/apps/v1/namespaces/`<namespace>`/deployments
* <b>Evaluation Type</b>: State comparison (desired vs actual)
* <b>Display Name in NetBrain</b>: Deployment Health

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Namespace
Defines the Kubernetes namespace from which deployments are retrieved.


## Deployment Name (Optional)
Used to filter a specific deployment if required.


# Key Fields Evaluated <a name="key-fields-evaluated"></a>
From deployment status:

* spec.replicas → Desired number of replicas
* status.replicas → Current number of replicas
* status.readyReplicas → Number of ready pods
* status.availableReplicas → Number of available pods


# Evaluation Logic <a name="evaluation-logic"></a>
## Health Condition
A deployment is considered healthy when:

`readyReplicas >= desiredReplicas`

## Unhealthy Condition
A deployment is considered unhealthy when:

`readyReplicas < desiredReplicas`


# Interpretation <a name="interpretation"></a>
* Healthy: All desired replicas are running and ready
* Degraded: Some replicas are not ready
* Unhealthy: Significant mismatch between desired and ready replicas


# Success Criteria <a name="success-criteria"></a>
The number of ready replicas matches or exceeds the desired replica count for the deployment.

# Alert Criteria <a name="alert-criteria"></a>
The number of ready replicas is less than the desired replica count. This condition may indicate rollout failures, resource constraints, or pod-level issues affecting application availability.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Rollout Validation
Ensure deployments are successfully rolled out with all replicas available.


## Use Case 2: Application Availability Monitoring
Detect partial or complete service degradation due to unavailable pods.


## Use Case 3: Troubleshooting Failed Deployments
Identify mismatches caused by:

* Image pull failures
* CrashLoopBackOff
* Insufficient cluster resources


## Use Case 4: Continuous Health Monitoring
Track deployment stability over time.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Deployment API: https://kubernetes.io/docs/reference/generated/kubernetes-api/
