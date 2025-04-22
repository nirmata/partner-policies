# Validate Namespace References (TIS0004)

## Overview

The TIS0004 suite comprises three Kyverno ClusterPolicies that ensure any namespace referenced within Istio resource fields actually exists in the cluster. Invalid namespaces in `exportTo` or `source.namespaces` can lead to unreachable services or mis‑applied policies.

### Policies

| Policy Name                                       | Resource Kind       | Validation                                                                                             | YAML File                                                     |
| ------------------------------------------------- | ------------------- | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------- |
| Check ServiceEntry ExportTo Namespace Exists      | ServiceEntry        | For each `spec.exportTo[]`, ensure each namespace (excluding `"."`) is a real namespace in the cluster | restrict-non-existent-namespace-for-serviceentry.yaml         |
| Check VirtualService ExportTo Namespace Exists    | VirtualService      | For each `spec.exportTo[]`, ensure each namespace (excluding `"."`) is a real namespace in the cluster | restrict-non-existent-namespace-for-virtual-service.yaml      |
| Check AuthorizationPolicy Source Namespaces Exist | AuthorizationPolicy | For each `spec.rules[].from[].source.namespaces[]`, ensure each namespace exists in the cluster        | restrict-non-existent-namespace-for-authorization-policy.yaml |

## Usage

Make sure Kyverno is installed in your Kubernetes cluster, then apply the policies:

```bash
kubectl apply -f restrict-non-existent-namespace-for-serviceentry.yaml
kubectl apply -f restrict-non-existent-namespace-for-virtual-service.yaml
kubectl apply -f restrict-non-existent-namespace-for-authorization-policy.yaml
```

## Web Reference

For more details, see:  
TIS0004 – Non‑Existent Namespace References  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0004)

## Conclusion

Validating namespace references in `exportTo` and `source.namespaces` fields prevents misconfigurations and ensures that traffic and access controls apply only to intended, existing namespaces. These Kyverno policies automate that check, maintaining the reliability of your service mesh.
