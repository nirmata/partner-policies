# Validate Root CA Certificate (TIS0005)

## Overview

The `validate-root-ca-cert` policy is a Kyverno ClusterPolicy that ensures the root CA certificate stored in the `root-ca` Secret within the `istio-system` namespace is valid and correctly formatted. It performs the following checks on the `ca-cert.pem` data field:

-   Certificate expiration (`notAfter`) must be in the future
-   Certificate must have a non‐empty subject
-   Certificate must include at least one SAN entry

If any of these conditions fail, the policy will deny the create or update operation, preventing an invalid root CA from being applied.

### Policy

| Policy Name           | Resource Kind | Validation                                                               | YAML File                  |
| --------------------- | ------------- | ------------------------------------------------------------------------ | -------------------------- |
| validate-root-ca-cert | Secret        | Deny if `ca-cert.pem` is expired, lacks a subject, or has no SAN entries | validate-root-ca-cert.yaml |

## Usage

Ensure you have Kyverno installed in your Kubernetes cluster, then apply the policy:

```bash
kubectl apply -f validate-root-ca-cert.yaml
```

## Web Reference

For more details, see:  
TIS0005 – Root CA Certificate Validation  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0005)

## Conclusion

A valid root CA certificate is fundamental for Istio's mTLS and overall service mesh security. This Kyverno policy automatically guards against expired or malformed root CA certificates, helping maintain uninterrupted, secure communication across your mesh.
