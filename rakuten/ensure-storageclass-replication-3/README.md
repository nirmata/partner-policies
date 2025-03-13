# Block Replication Change Policy

## Overview
The `block-replication-change` policy is a Kyverno ClusterPolicy designed to enforce data redundancy and resilience in Kubernetes by preventing the reduction of the replication factor in StorageClasses. This policy ensures that the replication factor remains at `3`, thereby safeguarding against potential data loss.

## Features
- **Prevents Replication Reduction**: Blocks any updates to StorageClasses that attempt to lower the replication factor from 3.

## Usage
To apply this policy, ensure that you have Kyverno installed in your Kubernetes cluster. You can apply the policy using the following command:
```bash
kubectl apply -f enforce-https-services.yaml
```
