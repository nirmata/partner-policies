# Enforce Single VirtualService Per Host
## Overview
The `enforce-single-virtualservice-per-host` policy is a Kyverno ClusterPolicy designed to ensure that only one VirtualService exists for each host within a namespace. This policy prevents configuration conflicts and ambiguity by enforcing a one-to-one relationship between hosts and VirtualServices.

The policy specifically:
- Validates that each host is defined in only one VirtualService per namespace
- Checks for host conflicts when creating or updating VirtualServices
- Prevents creation of VirtualServices with duplicate host definitions
- Provides clear guidance on resolving conflicts through VirtualService merging

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f enforce-single-virtualservice-per-host.yaml
```

## Web Reference
For more details, see:
TIS1105 - Multiple VirtualServices Define Same Host
This guidance from Tetrate outlines the importance of maintaining a single source of truth for host configurations and the potential issues that can arise from having multiple VirtualServices defining the same host.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1105)

## Conclusion
Maintaining a single VirtualService per host is crucial for a clear and maintainable service mesh configuration. This Kyverno policy ensures that host definitions remain unambiguous by preventing duplicate host configurations across multiple VirtualServices within the same namespace.
