# Validate Subset References in VirtualServices
## Overview
The `check-missing-subsets` policy is a Kyverno ClusterPolicy designed to ensure that all subset references in VirtualServices correspond to existing subsets defined in DestinationRules. This policy validates that any subset referenced in a VirtualService's route destinations exists in a DestinationRule within the same namespace, preventing misconfigurations that could cause traffic routing failures.

The policy specifically:
- Validates that all referenced subsets exist in DestinationRules
- Checks subset existence within the same namespace
- Prevents creation or updates of VirtualServices with invalid subset references
- Provides detailed information about existing and referenced subsets when validation fails

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f check-missing-subsets.yaml
```

## Web Reference
For more details, see:
TIS1106 - VirtualService References Non-Existent Subset
This guidance from Tetrate outlines the importance of validating subset references in VirtualServices and the potential issues that can arise from referencing non-existent subsets.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1106)

## Conclusion
Proper subset reference validation is crucial for maintaining a reliable service mesh. This Kyverno policy ensures that all VirtualServices reference only existing subsets defined in DestinationRules, preventing potential traffic routing failures and misconfigurations.
