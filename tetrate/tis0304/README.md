# Check Existing TLS Credentials

## Overview

The `check-existing-tls` policy is a Kyverno ClusterPolicy designed to ensure that TLS credentials referenced in a Gateway resource exist as Secrets in the same namespace before allowing creation or updates. This prevents misconfigurations that could lead to TLS handshake failures in Istio.

The policy specifically:

-   Runs on CREATE and UPDATE operations for `Gateway` resources
-   Extracts the Gateway's namespace and the list of TLS credential names from the manifest (`spec.servers[].tls.credentialName`)
-   Retrieves all Secret names in the same namespace
-   Denies the Gateway if any referenced credential is missing
-   Provides a clear error message listing missing and existing credentials

## Usage

To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and run:

```bash
kubectl apply -f check-existing-tls.yaml
```

## Web Reference

For more details, see:  
TIS0304 – Missing TLS Credentials  
This guidance from Tetrate explains why verifying the presence of TLS Secrets is critical to prevent Gateway TLS failures.  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0304)

## Conclusion

Validating the existence of TLS credentials as Kubernetes Secrets is essential for reliable TLS termination in your service mesh. This Kyverno policy helps prevent gateway misconfigurations and ensures secure communication.
