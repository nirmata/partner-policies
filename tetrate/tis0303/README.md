# Enforce Unique Gateway TLS Credentials

## Overview

The `check-duplicate-certificate-gateway` policy is a Kyverno ClusterPolicy designed to ensure that the same TLS `credentialName` is not reused across multiple Gateways in the same namespace. Reusing identical TLS credentials can lead to HTTP2 connection reuse errors (e.g., 404s) when clients maintain persistent connections.

The policy specifically:

-   Runs on CREATE and UPDATE operations for `Gateway` resources
-   Extracts the Gateway's namespace and the list of TLS credential names from the manifest
-   Retrieves existing TLS credential names from all Gateways in the same namespace
-   Denies the request if any credential in the manifest already exists on another Gateway
-   Provides a detailed error message listing both manifest and existing credentials when validation fails

## Usage

To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:

```bash
kubectl apply -f check-duplicate-certificate-gateway.yaml
```

## Web Reference

For more details, see:  
TIS0303 – Gateway TLS Credential Duplication  
This guidance from Tetrate explains why unique TLS credentials are critical for reliable HTTP2 routing and how to avoid client-side errors.  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0303)

## Conclusion

Enforcing unique TLS credentials for Gateways is essential to prevent connection reuse issues and ensure predictable ingress behavior. This Kyverno policy helps maintain a robust and error-free service mesh configuration.
