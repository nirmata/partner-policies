# Prevent Duplicate Gateway Host-Port Combinations
## Overview
The `prevent-duplicate-gateway-hostport` policy is a Kyverno ClusterPolicy designed to prevent the creation of Gateway resources with listeners that define the same host-port combination as existing Gateways. This policy ensures that no two Gateways can be created with the same hostname and port combination, which could lead to conflicts and undefined behavior in the service mesh.

The policy specifically:
- Validates that new Gateway resources don't have host-port conflicts with existing Gateways
- Checks for duplicate hostname and port combinations across all Gateway listeners
- Prevents creation of Gateways that would cause host-port conflicts

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f prevent-duplicate-gateway-hostport.yaml
```

## Web Reference
For more details, see:
TIS1501 - Gateway Has Duplicate Host-Port
This guidance from Tetrate outlines the importance of preventing host-port conflicts in Gateway configurations and the potential issues that can arise from duplicate host-port combinations.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1501)

## Conclusion
Preventing duplicate host-port combinations in Gateway configurations is crucial for maintaining a reliable service mesh. This Kyverno policy ensures that all Gateways have unique host-port combinations, preventing potential conflicts and undefined behavior in traffic routing.
