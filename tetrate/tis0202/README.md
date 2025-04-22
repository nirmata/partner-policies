# Validate Hosts in DestinationRules

## Overview

The `verify-destinationrule-hosts` policy is a Kyverno ClusterPolicy designed to ensure that DestinationRules reference valid VirtualServices in your Istio service mesh. This policy prevents misconfigurations where DestinationRules point to non-existent services, which can lead to routing failures.

The policy specifically:

-   Validates that each DestinationRule's host field points to an existing VirtualService
-   Prevents creation of DestinationRules with invalid service references
-   Helps avoid routing failures and service disruptions
-   Provides clear error messages listing available services when validation fails

## Usage

To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:

```bash
kubectl apply -f verify-destinationrule-hosts.yaml
```

## Web Reference

For more details, see:
TIS0202 - Invalid Host in DestinationRule
This guidance from Tetrate outlines the importance of ensuring DestinationRules reference valid VirtualServices and the potential issues that can arise from invalid host configurations.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0202)

## Conclusion

Maintaining valid host references in DestinationRules is crucial for ensuring proper routing in your service mesh. This Kyverno policy helps prevent configuration errors that could lead to routing failures and service disruptions.
