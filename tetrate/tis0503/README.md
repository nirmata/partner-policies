# Ensure Mesh‑Wide TLS Disabled

## Overview

The `ensure-meshwide-mtls-disable` policy is a Kyverno ClusterPolicy designed to enforce that any mesh‑wide DestinationRule (i.e., with `host: '*.cluster.local'`) explicitly disables mTLS by setting `spec.trafficPolicy.tls.mode` to `DISABLE`. This ensures that services that do not support mTLS or where mTLS is intentionally turned off do not inadvertently enable secure communication.

The policy specifically:

-   Runs on CREATE and UPDATE operations for `DestinationRule` resources
-   Extracts the `spec.host` and the `spec.trafficPolicy.tls.mode` (defaulting to empty)
-   Identifies mesh‑wide rules by checking for `host: '*.cluster.local'`
-   Denies any mesh‑wide DestinationRule whose `tls.mode` is not `DISABLE`
-   Provides a clear error message when validation fails

## Usage

To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and run:

```bash
kubectl apply -f ensure-meshwide-mtls-disable.yaml
```

## Web Reference

For more details, see:  
TIS0503 – Mesh‑Wide DestinationRule TLS Not Disabled  
This guidance from Tetrate outlines why disabling mTLS on global DestinationRules is necessary when integrating non‑mTLS‑capable services or managing legacy workloads.  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0503)

## Conclusion

Explicitly disabling mTLS in mesh‑wide DestinationRules is crucial for predictable traffic behavior when mTLS is undesired. This Kyverno policy helps maintain clear and intentional service configurations by preventing inadvertent secure communication.
