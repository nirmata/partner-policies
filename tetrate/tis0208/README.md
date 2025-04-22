# Allow Permissive Mode for PeerAuthentication

## Overview

The `allow-permissive-peerauth` policy is a Kyverno ClusterPolicy designed to ensure that when mTLS is configured in PeerAuthentication resources, it uses `PERMISSIVE` mode. This allows both mTLS-encrypted and plaintext traffic, facilitating gradual migration to strict mTLS. PeerAuthentication resources without any mTLS configuration are not affected by this policy.

The policy specifically:

-   Matches all `PeerAuthentication` resources
-   Checks for the presence of an `mtls` stanza
-   Validates that `spec.mtls.mode` is set to `PERMISSIVE`
-   Denies resources where mTLS is configured in any mode other than `PERMISSIVE`
-   Provides a clear error message when validation fails

## Usage

To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and run:

```bash
kubectl apply -f allow-permissive-peerauth.yaml
```

## Web Reference

For more details, see:  
TIS0208 – PeerAuth Permissive Mode Policy  
This guidance from Tetrate outlines why permitting both encrypted and plaintext traffic can ease the transition to strict mTLS while maintaining service availability.  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0208)

## Conclusion

Allowing permissive mTLS in PeerAuthentication resources is a useful step for introducing encryption without disrupting existing plaintext traffic. This Kyverno policy helps enforce the correct mode and provides a clear path toward a fully encrypted service mesh.
