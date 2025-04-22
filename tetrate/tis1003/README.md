# Validate Outbound Traffic Policy Mode
## Overview
The `validate-outbound-traffic-policy` policy is a Kyverno ClusterPolicy designed to ensure that all Sidecar resources have an explicitly defined outboundTrafficPolicy mode. This policy enforces that the mode must be set to either `ALLOW_ANY` or `REGISTRY_ONLY`, preventing ambiguous or insecure traffic configurations.

The policy specifically:
- Validates that outboundTrafficPolicy is explicitly defined in Sidecar resources
- Ensures the mode is set to either ALLOW_ANY or REGISTRY_ONLY
- Prevents creation of Sidecars with empty or invalid outbound traffic policies
- Helps maintain clear and secure outbound traffic configurations

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f check-for-empty-outboundTrafficPolicy.yaml
```

## Web Reference
For more details, see:
TIS1003 - Sidecar Has Empty Outbound Traffic Policy
This guidance from Tetrate outlines the importance of explicitly defining outbound traffic policies and the security implications of different policy modes.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1003)

## Conclusion
Proper configuration of outbound traffic policies is crucial for maintaining a secure service mesh. This Kyverno policy ensures that all Sidecar resources have explicit and valid outbound traffic policy modes, preventing potential security vulnerabilities and maintaining clear traffic control configurations.
