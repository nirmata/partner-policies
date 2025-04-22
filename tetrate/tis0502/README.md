# Check DestinationRule mTLS Disabled

## Overview

The `check-mtls-disabled` policy is a Kyverno ClusterPolicy designed to enforce that any TLS settings defined in a DestinationRule explicitly disable mTLS. This prevents unintended secure communication for services that do not support mTLS or where mTLS is intentionally turned off.

The policy specifically:

-   Runs on CREATE and UPDATE operations for `DestinationRule` resources
-   Validates that if `spec.trafficPolicy.tls.mode` is present, it must be set to `DISABLE`
-   Denies the request if the TLS `mode` is anything other than `DISABLE`
-   Provides a clear error message when validation fails

## Usage

To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and run:

```bash
kubectl apply -f check-mtls-disabled.yaml
```

## Web Reference

For more details, see:  
TIS0502 – DestinationRule mTLS Disabled  
This guidance from Tetrate explains why you may need to explicitly disable mTLS on certain DestinationRules and how misconfigurations can lead to traffic errors.  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0502)

## Conclusion

Explicitly disabling mTLS in DestinationRules is essential when integrating non‑mTLS‑capable services or managing legacy workloads. This Kyverno policy ensures that your DestinationRules do not inadvertently enable mTLS where it's undesired, maintaining predictable traffic behavior.
