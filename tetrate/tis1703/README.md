# Enforce FIPS-Compliant Image Policy

## Overview
The `enforce-fips-compliant-images` policy is a Kyverno ClusterPolicy designed to ensure that all container images for Kubernetes `Deployment` resources are pulled from the FIPS-compliant registry `fips-containers.istio.tetratelabs.com`. This aligns with Tetrate's guidelines for deploying Istio in environments that require FIPS 140-2 validated cryptography.

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using `kubectl`:
```bash
kubectl apply -f enforce-fips-compliant-images.yaml
```

## Conclusion
This policy enforces the use of FIPS-validated container images, ensuring that workloads meet compliance requirements and pass security audits in regulated environments.