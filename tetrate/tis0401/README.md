# Ensure Mesh‑Wide TLS Configured

## Overview

The `ensure-meshwide-mtls-present` policy is a Kyverno ClusterPolicy designed to enforce that any mesh‑wide DestinationRule (i.e., with `host: '*.cluster.local'`) defines TLS settings under `trafficPolicy`. By requiring mTLS or other TLS modes at the mesh‑wide level, this policy helps secure all service‑to‑service communication in your Istio service mesh.

The policy specifically:

-   Runs on CREATE and UPDATE operations for `DestinationRule` resources
-   Extracts the `spec.host` and `spec.trafficPolicy.tls.mode` fields
-   Identifies mesh‑wide rules by checking for `host: '*.cluster.local'`
-   Denies any mesh‑wide DestinationRule that does not configure TLS under `trafficPolicy`
-   Provides a clear error message when validation fails

## Usage

To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and run:

```bash
kubectl apply -f ensure-meshwide-mtls-present.yaml
```

## Web Reference

For more details, see:  
TIS0401 – Mesh‑Wide DestinationRule Missing TLS  
This guidance from Tetrate explains the importance of configuring TLS for mesh‑wide DestinationRules to enforce secure, encrypted service‑to‑service traffic.  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0401)

## Conclusion

Configuring TLS on mesh‑wide DestinationRules is a foundational step toward a zero‑trust Istio deployment. This Kyverno policy ensures that no global traffic rules are left unencrypted, promoting consistent security across your entire service mesh.
