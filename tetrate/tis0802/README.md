# Validate EnvoyFilter Patch Operations
## Overview
The `validate-envoyfilter-patch-operations` policy is a Kyverno ClusterPolicy designed to ensure proper usage of REMOVE operations in EnvoyFilter resources. This policy enforces that when a patch operation is set to REMOVE, the configPatches.applyTo field should not be set to ROUTE_CONFIGURATION or HTTP_ROUTE, as REMOVE operations are ignored for these filter types.

The policy specifically:
- Validates that REMOVE operations are not used with incompatible filter types
- Prevents REMOVE operations on ROUTE_CONFIGURATION and HTTP_ROUTE filter types
- Ensures proper usage of patch operations in EnvoyFilters
- Helps maintain effective EnvoyFilter configurations

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f validate-envoyfilter-patch-operations.yaml
```

## Web Reference
For more details, see:
TIS0802 - EnvoyFilter Uses REMOVE Operation with Invalid Filter Type
This guidance from Tetrate outlines the proper usage of REMOVE operations in EnvoyFilters and explains which filter types are incompatible with this operation.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0802)

## Conclusion
Proper configuration of EnvoyFilter operations is crucial for maintaining a reliable service mesh. This Kyverno policy ensures that REMOVE operations are not used with incompatible filter types, preventing ineffective configurations and maintaining proper Envoy proxy customization.
