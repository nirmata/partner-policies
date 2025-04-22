# Detect Duplicate Authentication Selectors (TIS0001)

## Overview

The TIS0001 suite comprises three Kyverno ClusterPolicies that ensure multiple Istio authentication resources do not share the same selector labels. When `PeerAuthentication`, `RequestAuthentication`, or `Telemetry` objects overlap on `spec.selector.matchLabels`, they can conflict, leading to unpredictable enforcement.

The suite includes:

-   **Detect Duplicate PeerAuthentication**  
    Matches all `PeerAuthentication` resources and denies creation or updates if:

    -   `spec.selector.matchLabels` is missing
    -   The `app` label in the selector is already used by another PeerAuthentication in the same namespace

-   **Detect Duplicate RequestAuthentication**  
    Matches all `RequestAuthentication` resources and denies creation or updates if:

    -   `spec.selector.matchLabels` is missing
    -   The `app` label in the selector is already used by another RequestAuthentication in the same namespace

-   **Detect Duplicate Telemetry**  
    Matches all `Telemetry` resources and denies creation or updates if:
    -   `spec.selector.matchLabels` is missing
    -   The `app` label in the selector is already used by another Telemetry in the same namespace

### Policies

| Policy Name                             | Resource Kind         | Validation                                                                                     | YAML File                                     |
| --------------------------------------- | --------------------- | ---------------------------------------------------------------------------------------------- | --------------------------------------------- |
| detect-duplicate-peer-authentication    | PeerAuthentication    | Deny if selector is missing or `app` label is duplicate across PeerAuthentication resources    | restrict-duplicate-peerauthentication.yaml    |
| detect-duplicate-request-authentication | RequestAuthentication | Deny if selector is missing or `app` label is duplicate across RequestAuthentication resources | restrict-duplicate-requestauthentication.yaml |
| detect-duplicate-telemetry              | Telemetry             | Deny if selector is missing or `app` label is duplicate across Telemetry resources             | restrict-duplicate-telemetry.yaml             |

## Usage

Ensure Kyverno is installed in your cluster, then apply each policy:

```bash
kubectl apply -f restrict-duplicate-peerauthentication.yaml
kubectl apply -f restrict-duplicate-requestauthentication.yaml
kubectl apply -f restrict-duplicate-telemetry.yaml
```

## Web Reference

For more details, see:  
TIS0001 – Duplicate Authentication Selector Detection  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0001)

## Conclusion

Preventing duplicate selector labels in authentication policies avoids overlapping rules and ensures deterministic mTLS and JWT enforcement across your service mesh.
