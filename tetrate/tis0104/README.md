# Enforce mTLS Requirements (TIS0104)

## Overview

The TIS0104 suite comprises three Kyverno ClusterPolicies that together ensure mutual TLS (mTLS) is uniformly enforced across your Istio service mesh:

1. **PeerAuthentication**: Require strict mTLS mode
2. **IstioOperator**: Require automatic mTLS in the control plane
3. **DestinationRule**: Require `ISTIO_MUTUAL` mode for traffic policies

By applying these policies, you guarantee end‑to‑end encryption, automatic certificate provisioning, and consistent workload‑level mTLS settings.

### Policies

| Policy Name                    | Resource Kind      | Validation                                                             | YAML File                                     |
| ------------------------------ | ------------------ | ---------------------------------------------------------------------- | --------------------------------------------- |
| peer-auth-strict-mtls-required | PeerAuthentication | `spec.mtls.mode` must be `STRICT`                                      | require-mtls-strict-perrauthentication.yaml   |
| istio-auto-mtls-required       | IstioOperator      | `spec.meshConfig.enableAutoMtls` must be `true`                        | require-mtls-istio-operator.yaml              |
| destinationrule-tls-mode       | DestinationRule    | If `spec.trafficPolicy.tls.mode` is present, it must be `ISTIO_MUTUAL` | require-tls-mode-mutual-destination-rule.yaml |

## Usage

Ensure Kyverno is installed in your Kubernetes cluster, then apply each policy:

```bash
kubectl apply -f require-mtls-strict-peerauthentication.yaml
kubectl apply -f require-mtls-istio-operator.yaml
kubectl apply -f require-tls-mode-mutual-destination-rule.yaml
```

## Web Reference

For detailed guidance on mTLS enforcement best practices, see:  
TIS0104 – mTLS Enforcement Suite  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0104)

## Conclusion

Enforcing strict mTLS, enabling automatic certificate rotation, and requiring `ISTIO_MUTUAL` mode on DestinationRules are foundational to a zero‑trust Istio deployment. The TIS0104 policy suite automates these checks, ensuring your mesh remains compliant with organizational security standards.
