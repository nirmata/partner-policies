# Validate App Selector Exists (TIS0003)

## Overview

The TIS0003 suite comprises three Kyverno ClusterPolicies that ensure the `spec.selector.matchLabels.app` field in Istio security resources corresponds to a running Pod in the same namespace. Without this validation, RequestAuthentication, PeerAuthentication, or Telemetry objects may target non‑existent applications, rendering security policies ineffective.

### Policies

| Policy Name                      | Resource Kind         | Validation                                                                            | YAML File                                      |
| -------------------------------- | --------------------- | ------------------------------------------------------------------------------------- | ---------------------------------------------- |
| validate-request-auth-app-exists | RequestAuthentication | Deny if `spec.selector.matchLabels.app` does not match any Pod label in the namespace | validate-requestauthentication-app-exists.yaml |
| validate-peer-auth-app-exists    | PeerAuthentication    | Deny if `spec.selector.matchLabels.app` does not match any Pod label in the namespace | validate-peerauthentication-app-exists.yaml    |
| validate-telemetry-app-exists    | Telemetry             | Deny if `spec.selector.matchLabels.app` does not match any Pod label in the namespace | validate-telemetry-app-exists.yaml             |

## Usage

Ensure Kyverno is installed in your Kubernetes cluster, then apply each policy:

```bash
kubectl apply -f validate-requestauthentication-app-exists.yaml
kubectl apply -f validate-peerauthentication-app-exists.yaml
kubectl apply -f validate-telemetry-app-exists.yaml
```

## Web Reference

For more details, see:  
TIS0003 – App Selector Existence  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0003)

## Conclusion

Validating that the `app` selector in RequestAuthentication, PeerAuthentication, and Telemetry resources matches an existing Pod ensures your security policies correctly apply to live workloads, maintaining effective and predictable enforcement.
