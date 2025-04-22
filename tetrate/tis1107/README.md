# Enforce Gateway Nomenclature in VirtualServices
## Overview
The `enforce-gateway-nomenclature` policy is a Kyverno ClusterPolicy designed to enforce the preferred Istio gateway reference format in VirtualServices. This policy ensures that all gateway references follow the format `[gateway namespace]/[gateway name]`, providing clarity and preventing potential conflicts when gateways with the same name exist in different namespaces.

The policy specifically:
- Validates that gateway references in VirtualServices use the namespace/name format
- Enforces consistent gateway naming conventions across the service mesh
- Prevents ambiguous gateway references that could lead to routing issues
- Helps maintain clear and explicit gateway references

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f enforce-gateway-nomenclature.yaml
```

## Web Reference
For more details, see:
TIS1107 - VirtualService Uses Ambiguous Gateway Reference
This guidance from Tetrate outlines the importance of using fully qualified gateway references in VirtualServices and the potential issues that can arise from ambiguous gateway references.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1107)

## Conclusion
Proper gateway nomenclature is crucial for maintaining a clear and reliable service mesh configuration. This Kyverno policy ensures that all VirtualServices use explicit gateway references in the format `namespace/name`, preventing ambiguity and potential routing issues.
