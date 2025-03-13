# Enforce Default StorageClass Policy

## Overview
The `enforce-default-storageclass` policy is designed to ensure that only one StorageClass can be designated as the default in a Kubernetes cluster. This policy enforces that the default `StorageClass` must be named `robin`, preventing any other `StorageClass` from being set as default.

## Key Features
- **Single Default StorageClass**: Only one StorageClass can be marked as default, which must be named `robin`.
- **Prevention of Multiple Defaults**: The policy denies the creation of additional default StorageClasses.
- **Modification Restrictions**: Once `robin` is set as the default, it cannot be modified.
- **Allow Removal of Default**: Other StorageClasses can have their default status removed, but `robin` remains protected.


## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML file using the following command:
```bash
kubectl apply -f enforce-https-services.yaml
```
