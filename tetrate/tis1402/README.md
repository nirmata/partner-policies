# Enforce Valid Service References in HTTPRoutes
## Overview
The `enforce-valid-service-refs` policy is a Kyverno ClusterPolicy designed to ensure that all HTTPRoute resources reference valid Kubernetes Services within the same namespace. This policy validates that any Service referenced in an HTTPRoute's `backendRefs` exists in the cluster, preventing misconfigurations and potential routing issues.

The policy specifically:
- Validates that all Service references in HTTPRoute backendRefs exist in the same namespace
- Checks both explicit Service kind references and implicit Service references
- Prevents creation or updates of HTTPRoutes with invalid Service references

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f enforce-valid-service-refs.yaml
```

## Web Reference
For more details, see:
TIS1402 - HTTPRoute References Non-Existent Service
This guidance from Tetrate outlines the importance of validating Service references in HTTPRoute configurations and the potential issues that can arise from referencing non-existent services.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1402)

## Conclusion
Validating Service references in HTTPRoute configurations is crucial for maintaining a reliable service mesh. This Kyverno policy ensures that all HTTPRoutes reference existing Services, preventing potential routing issues and misconfigurations.
