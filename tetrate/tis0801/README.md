# Validate EnvoyFilter Patch Operations

## Overview

The `validate-envoyfilter-add-operations` policy is a Kyverno ClusterPolicy designed to prevent ineffective EnvoyFilter patches by ensuring that when `patch.operation` is set to `ADD`, the `configPatches.applyTo` field is not one of the types that Envoy ignores (namely `ROUTE_CONFIGURATION` or `HTTP_ROUTE`). Without this check, ADD operations against these targets silently have no effect, leading to confusing misconfigurations.

The policy specifically:

-   Matches all `EnvoyFilter` resources
-   Iterates through each entry in `spec.configPatches`
-   Checks if `patch.operation == ADD`
-   Denies the request if `applyTo` is `ROUTE_CONFIGURATION` or `HTTP_ROUTE` under an ADD operation
-   Provides a clear error message indicating the unsupported combination

## Usage

To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and run:

```bash
kubectl apply -f check-applyTo-incase-of-ADD-operation.yaml
```

## Web Reference

For more details, see:  
TIS0801 – EnvoyFilter ADD Operation Compatibility  
This guidance from Tetrate explains why certain `applyTo` targets are ignored when using the ADD operation and how to avoid silent failures in your EnvoyFilter patches.  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0801)

## Conclusion

Validating the compatibility of `applyTo` with the ADD operation in EnvoyFilter patches is essential to ensure your filters are applied as intended. This Kyverno policy catches unsupported combinations early, helping maintain predictable Envoy behavior.
