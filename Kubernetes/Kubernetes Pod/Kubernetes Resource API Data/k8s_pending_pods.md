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
The <b>Pending Pod Detection</b> API identifies whether a specific Kubernetes pod is stuck in the Pending state.

A pod in Pending state indicates that it has been accepted by the Kubernetes system but has not yet been scheduled onto a node or cannot start successfully.

Common causes include:

* Insufficient CPU or memory resources
* Node constraints or taints
* Volume binding issues
* Image pull delays

This API retrieves pod status directly from the Kubernetes API server to determine if the pod is pending.


# Metric Info <a name="metric-info"></a>
* <b>Resource Type</b>: Pod (v1)
* <b>Source</b>: Kubernetes API Server
* <b>Endpoint</b>: /api/v1/namespaces/{namespace}/pods/{pod}
* <b>Evaluation Type</b>: State inspection
* <b>Display Name in NetBrain</b>: Pending Pods Detection

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Namespace
Defines the Kubernetes namespace of the pod.


## Pod Name
Defines the target pod.


# Key Fields Evaluated <a name="key-fields-evaluated"></a>
* status.phase → Pod lifecycle phase
* status.conditions → Scheduling and readiness conditions
* status.containerStatuses[].state → Container-level state


# Evaluation Logic <a name="evaluation-logic"></a>
## Pending Condition
`status.phase = "Pending"`

## Non-Pending Condition
`status.phase != "Pending"`


# Interpretation <a name="interpretation"></a>
* Pending → Pod is not scheduled or not started
* Running → Pod is successfully scheduled and running
* Failed → Pod execution failed


# Success Criteria <a name="success-criteria"></a>
The pod is not in a Pending state and has transitioned to Running or another valid terminal state.

# Alert Criteria <a name="alert-criteria"></a>
The pod is in a Pending state. This condition may indicate scheduling failures, insufficient resources, or configuration issues preventing the pod from starting.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Scheduling Failure Detection
Identify pods that cannot be scheduled due to resource shortages.


## Use Case 2: Deployment Troubleshooting
Detect pods stuck during rollout.


## Use Case 3: Resource Constraint Analysis
Correlate pending pods with node CPU, memory, or disk utilization.


## Use Case 4: Cluster Capacity Monitoring
Identify when cluster resources are insufficient to handle workloads.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Pod API Reference: https://kubernetes.io/docs/reference/generated/kubernetes-api/
