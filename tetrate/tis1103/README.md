# Validate VirtualService Weights
## Overview
The `validate-virtualservice-weights` policy is a Kyverno ClusterPolicy designed to enforce proper usage of weight fields in VirtualService configurations. This policy ensures that weight fields are only specified when there are multiple destinations, as Istio automatically assigns a weight of 100 to single destinations.

The policy specifically:
- Validates that weight fields are omitted for single-destination routes
- Ensures weight fields are only used when multiple destinations are present
- Prevents unnecessary weight specifications that could cause confusion
- Helps maintain clean and efficient VirtualService configurations

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f validate-virtualservice-weights.yaml
```

## Web Reference
For more details, see:
TIS1103 - VirtualService Has Unnecessary Weight Field
This guidance from Tetrate outlines the best practices for using weight fields in VirtualServices and explains why weights should be omitted for single-destination routes.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1103)

## Conclusion
Proper usage of weight fields in VirtualServices is crucial for maintaining clear and efficient service mesh configurations. This Kyverno policy ensures that weight fields are only used when necessary, preventing confusion and maintaining consistency with Istio's automatic weight assignment for single destinations.
