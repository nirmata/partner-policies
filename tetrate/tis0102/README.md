# Validate HTTP and gRPC Methods (TIS0102)

## Overview

The TIS0102 suite comprises two Kyverno ClusterPolicies that ensure correct method specifications in your Istio configuration:

1. **AuthorizationPolicy Method Validation**  
   Ensures that in `AuthorizationPolicy` resources, the `spec.rules[].to[].operation.methods[]` field contains only valid HTTP methods or properly formatted gRPC methods (i.e., `/package.service/method`).

2. **VirtualService HTTP Method Validation**  
   Ensures that in `VirtualService` resources, HTTP match rules under `spec.http[*].match[*].method.type` use only allowed HTTP methods.

By applying these policies, you prevent misconfigurations and unintended access behaviors caused by invalid or misspelled method names.

### Policies

| Policy Name                           | Resource Kind       | Validation                                                                                                                            | YAML File                                         |
| ------------------------------------- | ------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| validate-authorization-policy-methods | AuthorizationPolicy | `spec.rules[].to[].operation.methods[]` must be one of the allowed HTTP methods or match the gRPC pattern `^/package.service/method$` | restrict-invalid-method-authorization-policy.yaml |
| validate-vs-http-methods              | VirtualService      | `spec.http[*].match[*].method.type` must be one of: `GET`, `HEAD`, `POST`, `PUT`, `DELETE`, `CONNECT`, `OPTIONS`, `TRACE`, or `PATCH` | restrict-invalid-method-virtualservice.yaml       |

## Usage

Ensure Kyverno is installed in your Kubernetes cluster, then apply each policy:

```bash
kubectl apply -f restrict-invalid-method-authorization-policy.yaml
kubectl apply -f restrict-invalid-method-virtualservice.yaml
```

## Web Reference

For more details, see:  
TIS0102 – Method Specification Validation  
This guidance from Tetrate explains why validating HTTP and gRPC method names is critical for secure and predictable routing in your service mesh.  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0102)

## Conclusion

Validating method names in `AuthorizationPolicy` and `VirtualService` resources helps maintain correct access control and routing behavior. The TIS0102 policy suite catches invalid or unsupported methods early, ensuring consistent and secure traffic management across your Istio mesh.
