# Validate VirtualService Hosts Exist in Service Registry
## Overview
The `validate-virtualservice-hosts` policy is a Kyverno ClusterPolicy designed to ensure that all hosts referenced in VirtualServices correspond to existing services in the Kubernetes service registry. This policy prevents routing failures by validating that hosts are properly configured and exist in the cluster.

The policy specifically:
- Validates that all hosts in VirtualServices reference existing services
- Checks the service registry for each host's existence
- Prevents creation or updates of VirtualServices with non-existent hosts
- Helps maintain reliable service routing configurations

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f validate-virtualservice-hosts.yaml
```

## Web Reference
For more details, see:
TIS1001 - VirtualService References Non-Existent Service
This guidance from Tetrate outlines the importance of validating host references in VirtualServices and explains the potential issues that can arise from referencing non-existent services.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1001)

## Conclusion
Proper validation of VirtualService hosts is crucial for maintaining a reliable service mesh. This Kyverno policy ensures that all VirtualServices reference existing services in the registry, preventing potential routing failures and maintaining clear service routing configurations.
