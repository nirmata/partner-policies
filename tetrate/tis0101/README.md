# Validate Host Namespace (TIS0101)

## Overview

The TIS0101 suite comprises two Kyverno ClusterPolicies that ensure hosts declared in ServiceEntry and VirtualService resources reference an existing Kubernetes namespace. Without this check, a mis‑typed namespace in a host FQDN (e.g. `my-svc.wrong-ns.svc.cluster.local`) can lead to unreachable services.

### Policies

| Policy Name                            | Resource Kind  | Validation                                                                                         | YAML File                                                 |
| -------------------------------------- | -------------- | -------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| validate-serviceentry-host-namespace   | ServiceEntry   | For each `spec.hosts[]`, extract the `<namespace>` from `*.svc.cluster.local` and ensure it exists | restrict-non-existent-namespace-host-serviecentry.yaml    |
| validate-virtualservice-host-namespace | VirtualService | For each `spec.hosts[]`, extract the `<namespace>` from `*.svc.cluster.local` and ensure it exists | restrict-non-existent-namespace-host-virtual-service.yaml |

## Usage

Ensure Kyverno is installed in your Kubernetes cluster, then apply each policy:

```bash
kubectl apply -f restrict-non-existent-namespace-host-serviecentry.yaml
kubectl apply -f restrict-non-existent-namespace-host-virtual-service.yaml
```

## Web Reference

For more details, see:  
TIS0101 – Non‑Existent Namespace in Host FQDN  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0101)

## Conclusion

Validating that hosts in ServiceEntry and VirtualService resources reference real namespaces prevents routing to non‑existent services and ensures reliable connectivity in your service mesh.
