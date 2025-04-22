# Validate EnvoyFilter Replace Operations
## Overview
The `validate-envoyfilter-replace-operations` policy is a Kyverno ClusterPolicy designed to ensure proper usage of REPLACE operations in EnvoyFilter resources. This policy enforces that when a patch operation is set to REPLACE, the configPatches.applyTo field must be set to either HTTP_FILTER or NETWORK_FILTER, as these are the only valid filter types for REPLACE operations.

The policy specifically:
- Validates that REPLACE operations are only used with compatible filter types
- Ensures configPatches.applyTo is set to HTTP_FILTER or NETWORK_FILTER for REPLACE operations
- Prevents creation of EnvoyFilters with invalid REPLACE operation configurations
- Helps maintain proper EnvoyFilter configurations

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f validate-envoyfilter-replace-operations.yaml
```

## Web Reference
For more details, see:
TIS0803 - EnvoyFilter Uses REPLACE Operation with Invalid Filter Type
This guidance from Tetrate outlines the proper usage of REPLACE operations in EnvoyFilters and explains the limitations of this operation type.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0803)

## Conclusion
Proper configuration of EnvoyFilter operations is crucial for maintaining a reliable service mesh. This Kyverno policy ensures that REPLACE operations are only used with compatible filter types, preventing potential configuration errors and maintaining proper Envoy proxy customization.
