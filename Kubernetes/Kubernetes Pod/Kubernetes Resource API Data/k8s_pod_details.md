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
The <b>Pod Metadata and Status</b> API retrieves detailed information about a specific Kubernetes pod, including its configuration, current state, and runtime conditions.

This API provides a real-time view of pod health and is commonly used for:

* Troubleshooting application issues
* Inspecting pod lifecycle state
* Validating deployment behavior
It directly queries the Kubernetes API server for authoritative pod state.



# Metric Info <a name="metric-info"></a>
* <b>Resource Type</b>: Pod (v1)
* <b>Source</b>: Kubernetes API Server
* <b>Endpoint</b>: /api/v1/namespaces/{namespace}/pods/{pod}
* <b>Evaluation Type</b>: State inspection
* <b>Display Name in NetBrain</b>: Pod Metadata and Status

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Namespace
Defines the Kubernetes namespace of the pod.


## Pod Name
Defines the target pod.

# Key Fields Evaluated <a name="key-fields-evaluated"></a>
## Metadata
* metadata.name → Pod name
* metadata.namespace → Namespace
* metadata.labels → Labels
* metadata.annotations → Annotations

## Spec
* spec.nodeName → Node where pod is scheduled
* spec.containers → Container definitions
* spec.restartPolicy → Restart behavior

## Status
* status.phase → Pod phase
  * Pending
  * Running
  * Succeeded
  * Failed
  * Unknown
* status.conditions:
  * Ready
  * Initialized
  * ContainersReady
  * PodScheduled
* status.containerStatuses:
  * ready → Container readiness
  * restartCount → Number of restarts
  * state:
      * Running
      * Waiting
      * Terminated

# Evaluation Logic <a name="evaluation-logic"></a>
## Healthy Condition
status.phase = "Running"
AND all containers are ready

## Degraded Condition
status.phase = "Running"
AND one or more containers are not ready


## Unhealthy Condition
status.phase IN ("Pending", "Failed", "Unknown")
OR container state indicates Waiting or Terminated with errors


# Interpretation <a name="interpretation"></a>
* Running + Ready → Pod is healthy
* Running but not Ready → Partial availability
* Pending → Scheduling or resource issue
* Failed → Execution failure
* Unknown → Node or communication issue


# Success Criteria <a name="success-criteria"></a>
The pod is in a Running state and all containers are in a Ready condition.

# Alert Criteria <a name="alert-criteria"></a>
The pod is not in a healthy state. This includes conditions where the pod is Pending, Failed, Unknown, or containers are not ready. Such conditions may indicate scheduling issues, runtime failures, or application errors.

# Use Case Examples <a name="user-case-examples"></a>
## Use Case 1: Pod Health Monitoring
Determine whether a pod is fully operational.


## Use Case 2: Troubleshooting Failures
Inspect container states such as CrashLoopBackOff or ImagePullBackOff.


## Use Case 3: Deployment Validation
Verify that newly created pods are running and ready.


## Use Case 4: Restart Analysis
Track container restart counts to identify unstable workloads.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Pod API Reference: https://kubernetes.io/docs/reference/generated/kubernetes-api/