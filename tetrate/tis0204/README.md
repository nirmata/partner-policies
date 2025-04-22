# Validate mTLS Settings for DestinationRules

## Overview

The `check-mtls-overrides` policy is a Kyverno ClusterPolicy designed to ensure consistent mutual TLS (mTLS) configurations across your Istio service mesh. It verifies that local DestinationRules do not conflict with the global mTLS settings, preventing unintended overrides that can lead to inconsistent security behavior.

The policy specifically:

-   Extracts the local mTLS mode from a DestinationRule's `trafficPolicy.tls.mode`
-   Retrieves the global mTLS mode from the default DestinationRule (`*.svc.cluster.local`)
-   Denies any DestinationRule whose mTLS mode does not align with the global setting
-   Provides clear error messages when validation fails

## Usage

To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:

```bash
kubectl apply -f check-mtls-overrides.yaml
```

## Web Reference

For more details, see:  
TIS0204 – mTLS Setting Overrides  
This guidance from Tetrate outlines the importance of maintaining consistent mTLS configurations in DestinationRules and the risks of conflicting overrides.  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0204)

## Conclusion

Maintaining consistent mTLS settings is crucial for the security and reliability of your service mesh. This Kyverno policy helps prevent local overrides from diverging from your global mTLS posture, ensuring predictable behavior and robust communication security.
