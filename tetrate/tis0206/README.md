# Enforce Strict Mode for PeerAuthentication

## Overview

The `allow-permissive-strict-peerauth` policy is a Kyverno ClusterPolicy designed to enforce strict mutual TLS (mTLS) mode in your Istio mesh's PeerAuthentication resources. When mTLS is configured, this policy ensures the mode is set to `STRICT`, disallowing plaintext fallback and guaranteeing encrypted traffic. PeerAuthentication resources without an `mtls` stanza are unaffected.

The policy specifically:

-   Matches all PeerAuthentication resources
-   Checks for the presence of an `mtls` configuration
-   Validates that `spec.mtls.mode` equals `STRICT`
-   Denies any PeerAuthentication that configures mTLS in a non-STRICT mode
-   Provides a clear error message when validation fails

## Usage

To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and run:

```bash
kubectl apply -f allow-permissive-strict-peerauth.yaml
```

## Web Reference

For more details, see:  
TIS0206 – PeerAuth Strict Mode Enforcement  
This guidance from Tetrate outlines why enforcing strict mTLS is critical for service-to-service security and the pitfalls of allowing plaintext traffic.  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0206)

## Conclusion

Enforcing strict mTLS for PeerAuthentication resources is vital for end‑to‑end encryption in your service mesh. This Kyverno policy helps maintain a robust security posture by ensuring no unintended plaintext traffic is allowed.
