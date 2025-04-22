# Enforce COMPLIANCE_POLICY for FIPS Mode
## Overview
The check-compliance-policy-env-chainsaw policy is a Kyverno ClusterPolicy designed to enforce that all Kubernetes Deployments include the environment variable `COMPLIANCE_POLICY` set to `fips-140-2`.

This ensures Istio components, such as `istiod`, operate in strict FIPS 140-2 mode — restricting TLS to version 1.2 and limiting cipher suites to FIPS-approved algorithms.

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f check-compliance-policy-env-chainsaw.yaml
```
## Web Reference
For more details, see:
TIS1701 - Compliance Policy Is Missing, Invalid, or Not Set to Enforce FIPS 140-2 Requirements
This guidance from Tetrate describes the need to set COMPLIANCE_POLICY=fips-140-2 to enable strict FIPS enforcement in Istio.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1701)

## Conclusion
Setting the COMPLIANCE_POLICY environment variable ensures your Istio deployments enforce FIPS 140-2 compliance across the mesh. This Kyverno policy guarantees that misconfigured or missing environment variables are blocked, maintaining secure and compliant operations.