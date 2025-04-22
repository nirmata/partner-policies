# Validate GatewayClass References
## Overview
The `check-existing-gatewayclass` policy is a Kyverno ClusterPolicy designed to ensure that all Gateway resources reference valid GatewayClass resources. The policy validates that any GatewayClass specified in a Gateway's `gatewayClassName` field exists in the cluster.

This policy helps prevent misconfigurations and potential routing issues by ensuring that Gateways only reference existing GatewayClasses.

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f check-gatewayclass-exists.yaml
```

## Web Reference
For more details, see:
TIS1504 - Gateway References Non-Existent GatewayClass
This guidance from Tetrate outlines the importance of validating GatewayClass references in Gateway configurations.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1504)

## Conclusion
Validating GatewayClass references in Gateway configurations is crucial for maintaining a reliable service mesh. This Kyverno policy ensures that all Gateways reference existing GatewayClasses, preventing potential routing issues and misconfigurations.
