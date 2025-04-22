# Validate WorkloadEntry ServiceEntry Address Mapping
## Overview
The `validate-workloadentry-serviceentry-address-mapping` policy is a Kyverno ClusterPolicy designed to ensure that each WorkloadEntry's address is properly mapped to a corresponding ServiceEntry. This policy validates that every WorkloadEntry address is included in at least one ServiceEntry's addresses field, preventing misconfigurations that could lead to routing issues in the service mesh.

The policy specifically:
- Validates that each WorkloadEntry address exists in a ServiceEntry's addresses field
- Checks for address mappings within the same namespace
- Prevents creation of WorkloadEntries without proper ServiceEntry mappings
- Provides detailed debug information when validation fails

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f check-workload-serviceentry-mapping.yaml
```

## Web Reference
For more details, see:
TIS1201 - WorkloadEntry Address Not Mapped to ServiceEntry
This guidance from Tetrate outlines the importance of proper address mapping between WorkloadEntries and ServiceEntries and the potential issues that can arise from misconfigured mappings.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1201)

## Conclusion
Proper address mapping between WorkloadEntries and ServiceEntries is crucial for maintaining a reliable service mesh. This Kyverno policy ensures that all WorkloadEntries are properly mapped to ServiceEntries, preventing potential routing issues and misconfigurations.
