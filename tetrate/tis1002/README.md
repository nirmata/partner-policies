# Validate Global Sidecar Configuration
## Overview
The `validate-global-sidecar-configuration` policy is a Kyverno ClusterPolicy designed to ensure proper configuration of global Sidecar resources. This policy enforces that Sidecars with global egress configuration (using `*/*` hosts) should not include a workloadSelector, particularly in the istio-system namespace, to prevent potential conflicts and misconfigurations.

The policy specifically:
- Validates that global Sidecars (with `*/*` egress hosts) do not have workload selectors
- Ensures proper configuration of global egress settings
- Prevents creation of Sidecars with conflicting global and workload-specific settings
- Helps maintain clear and consistent Sidecar configurations

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f check-global-sidecar-no-workload-selector.yaml
```

## Web Reference
For more details, see:
TIS1002 - Global Sidecar Has Workload Selector
This guidance from Tetrate outlines the best practices for configuring global Sidecars and explains why workload selectors should not be used with global egress configurations.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1002)

## Conclusion
Proper configuration of global Sidecars is crucial for maintaining a reliable service mesh. This Kyverno policy ensures that global Sidecar resources are configured correctly by preventing the use of workload selectors with global egress settings, maintaining clear and consistent traffic control configurations.
