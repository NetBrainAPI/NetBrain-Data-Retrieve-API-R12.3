# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Aggregation Function](#aggregation-function)
- [Supported Functions](#supported-functions)
- [Evaluation Logic](#evaluation-logic)
- [Interpretation](#interpretation)
- [Success Criteria](#success-criteria)
- [Alert Criteria](#alert-criteria)
- [Use Case Examples](#use-case-examples)
- [Reference](#reference)


# Overview <a name="overview"></a>
The <b>Privileged Container Detection</b> API identifies containers running with elevated privileges within a Kubernetes pod.

Containers configured with privileged: true have access to host-level resources and can bypass many of the isolation mechanisms provided by the container runtime. This significantly increases the attack surface and security risk.

This API helps detect such configurations and enforce security best practices.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: kube_pod_container_security_context_privileged
* <b>Source</b>: kube-state-metrics
* <b>Metric Type</b>: Gauge (binary: 0 or 1)
* <b>Evaluation Type</b>: Instant query
* <b>Display Name in NetBrain</b>: Container Security Privilege Context

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Namespace
Defines the Kubernetes namespace.


## Pod Name
Defines the target pod.


## Unit
* Binary (0 or 1)



# Aggregation Function <a name="aggregation-function"></a>
## Threshold
* `>= 1` → Privileged container detected


# Supported Functions <a name="supported-functions"></a>
## Instant Vector Aggregations
* sum(v)
* count(v)
* max(v)
* topk(k, v)


# Evaluation Logic <a name="evaluation-logic"></a>
## PromQL Conceptual Expression (Container Level)
```
kube_pod_container_security_context_privileged{
  namespace="$NAME_SPACE",
  pod="$KUBNAME"
} == 1
```

## PromQL Conceptual Expression (Pod Level)
```
sum(
  kube_pod_container_security_context_privileged{
    namespace="$NAME_SPACE",
    pod="$KUBNAME"
  }
) >= 1
```


# Interpretation <a name="interpretation"></a>
* Value = 1 → Container is running in privileged mode
* Value = 0 → Container is not privileged


# Success Criteria <a name="success-criteria"></a>
No containers within the pod are running in privileged mode.

# Alert Criteria <a name="alert-criteria"></a>
One or more containers within the pod are running in privileged mode. This condition increases the risk of host compromise, as privileged containers have elevated access to system resources and may bypass standard isolation mechanisms.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Security Compliance
Ensure workloads adhere to security policies by avoiding privileged containers.


## Use Case 2: Risk Detection
Identify containers with elevated access to host resources.


## Use Case 3: Policy Enforcement
Support enforcement of Pod Security Standards or admission controls.


## Use Case 4: Audit and Governance
Track and audit privileged workloads across environments.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Pod Security Standards: https://kubernetes.io/docs/concepts/security/pod-security-standards/
* kube-state-metrics: https://github.com/kubernetes/kube-state-metrics
