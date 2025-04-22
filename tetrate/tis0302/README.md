# Check Gateway Selector

## Overview

The `check-gateway-selector` policy is a Kyverno ClusterPolicy designed to ensure that a Gateway's selector matches at least one running workload in the same namespace. Without a matching ingress pod, the Gateway will be ineffective, potentially causing unreachable services or misconfigurations.

The policy specifically:

-   Runs on CREATE and UPDATE operations for Gateway resources
-   Extracts the Gateway's namespace and `spec.selector.istio` label
-   Queries the Kubernetes API for pods matching `istio=<label>` in that namespace
-   Denies the Gateway if no matching pods are found
-   Provides a clear, actionable error message when validation fails

## Usage

To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and run:

```bash
kubectl apply -f check-gateway-selector.yaml
```

## Web Reference

For more details, see:  
TIS0302 – Gateway Selector Misconfiguration  
This guidance from Tetrate explains why ensuring Gateway selectors align with actual workloads is critical for reliable ingress traffic handling.  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0302)

## Conclusion

Validating that Gateway selectors target existing ingress workloads is essential for a functional service mesh. This Kyverno policy prevents dead‑end Gateways by verifying that the specified selector label matches at least one running pod.
