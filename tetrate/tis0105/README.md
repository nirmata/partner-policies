# Validate Service Accounts in AuthorizationPolicy

## Overview

The `check-existing-service-account` policy is a Kyverno ClusterPolicy designed to ensure that any ServiceAccount referenced in an `AuthorizationPolicy` actually exists within the cluster. This prevents misconfigurations where policies reference non-existent ServiceAccounts, which can lead to unintended access behaviors or errors.

The policy specifically:

-   Runs on **CREATE** and **UPDATE** operations for `AuthorizationPolicy` resources
-   Extracts principals from `spec.rules[].from[].source.principals[]` that match the pattern `cluster.local/ns/.../sa/...`
-   Retrieves all existing ServiceAccount names in the cluster
-   Denies the request if any referenced ServiceAccount is not found
-   Provides a clear error message listing missing and existing ServiceAccounts

## Usage

To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and run:

```bash
kubectl apply -f check-existing-service-account.yaml
```

## Web Reference

For more details, see:  
TIS0105 – ServiceAccount Reference Validation  
This guidance from Tetrate explains why verifying referenced ServiceAccounts is critical for correct and secure AuthorizationPolicies.  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0105)

## Conclusion

Verifying that ServiceAccounts referenced in AuthorizationPolicies actually exist is essential for reliable access control. This Kyverno policy helps maintain accurate and secure authorization configurations in your service mesh.
