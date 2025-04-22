# Validate Gateway References in HTTPRoutes
## Overview
The `check-existing-gateway` policy is a Kyverno ClusterPolicy designed to ensure that all HTTPRoute resources reference valid Gateway resources within the same namespace. This policy validates that any Gateway referenced in an HTTPRoute's `parentRefs` exists in the cluster, preventing misconfigurations and potential routing issues.

The policy specifically:
- Validates that all Gateway references in HTTPRoute parentRefs exist in the same namespace
- Checks for the existence of referenced Gateways before allowing HTTPRoute creation
- Prevents creation of HTTPRoutes with invalid Gateway references

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f check-existing-gateway.yaml
```

## Web Reference
For more details, see:
TIS1401 - HTTPRoute References Non-Existent Gateway
This guidance from Tetrate outlines the importance of validating Gateway references in HTTPRoute configurations and the potential issues that can arise from referencing non-existent Gateways.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1401)

## Conclusion
Validating Gateway references in HTTPRoute configurations is crucial for maintaining a reliable service mesh. This Kyverno policy ensures that all HTTPRoutes reference existing Gateways, preventing potential routing issues and misconfigurations.
