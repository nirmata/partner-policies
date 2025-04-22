# Restrict TLS to FIPS-Compliant Settings
## Overview
The restrict-fips-tls-settings policy is a Kyverno ClusterPolicy designed to ensure that all Istio Gateway resources adhere to strict FIPS 140-2 requirements. Specifically, it validates that the TLS settings:

Restrict both minProtocolVersion and maxProtocolVersion to TLSV1_2

Use only the four FIPS-approved ECDHE AES-GCM cipher suites

This policy helps maintain secure and compliant TLS configurations across your service mesh.

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f restrict-fips-tls-settings.yaml
```
## Web Reference
For more details, see:
TIS1702 - Gateway’s TLS Configuration Does Not Comply with FIPS 140-2 Requirements
This guidance from Tetrate outlines how to ensure strict FIPS compliance for inbound connections in Istio Gateway configurations.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1702)

## Conclusion
Enforcing FIPS-compliant TLS settings is critical for secure and regulatory-compliant service meshes. This Kyverno policy ensures that all Istio Gateways meet those requirements by validating protocol versions and cipher suites accordingly.

