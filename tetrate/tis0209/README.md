# Subset Lacks Labels

## Overview

The `check-subset-labels` policy is a Kyverno ClusterPolicy designed to enforce that each subset defined in a DestinationRule includes labels. Without labels, subsets cannot be properly matched, leading to routing misconfigurations.

The policy specifically:

-   Matches all `DestinationRule` resources with defined subsets
-   Validates that each subset has a non-empty `labels` field
-   Denies any `DestinationRule` where one or more subsets lack labels
-   Provides a clear error message when validation fails

## Usage

To apply this policy, ensure Kyverno is installed in your Kubernetes cluster and run:

```bash
kubectl apply -f check-subset-labels.yaml
```

## Web Reference

For more details, see:  
TIS0209 – Subset Lacks Labels  
This guidance from Tetrate outlines the necessity of labeling subsets in DestinationRules to maintain correct routing behavior in the service mesh.  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0209)

## Conclusion

Proper labeling of subsets in DestinationRules is crucial for predictable traffic management in your Istio service mesh. This Kyverno policy ensures subsets are never defined without labels, preventing potential routing issues.
