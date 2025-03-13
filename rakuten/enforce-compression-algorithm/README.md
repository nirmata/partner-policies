# Enforce StorageClass Compression Policy

## Overview
The `enforce-storageclass-compression` policy is a Kyverno ClusterPolicy designed to ensure that all `StorageClass` objects named with the prefix `robin` have their compression algorithm set to `LZ4`. This policy helps maintain consistent storage performance and efficiency across your Kubernetes cluster.

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using `kubectl`:
```bash
kubectl apply -f enforce-compression-algorithm.yaml
```

## Conclusion
This policy is essential for ensuring that your storage classes meet the required compression standards, thereby optimizing storage usage and performance.
