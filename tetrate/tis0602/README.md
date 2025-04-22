# Validate Service Port AppProtocol (Regex)

## Overview

The `validate-service-port-names-regex` policy is a Kyverno ClusterPolicy designed to enforce a consistent naming convention for the `appProtocol` field on Kubernetes Service ports. It uses a regular expression to ensure each `appProtocol` follows the `protocol[-suffix]` format, where `protocol` is one of:

-   http
-   http2
-   https
-   tcp
-   tls
-   grpc
-   grpc-web
-   mongo
-   mysql
-   redis

By validating `appProtocol`, this policy helps Istio and other service mesh components correctly infer protocols and route traffic accordingly.

## Usage

To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and run:

```bash
kubectl apply -f check-appprotocal-have-valid-protocol.yaml
```

## Web Reference

For more details, see:  
TIS0602 – Service Port AppProtocol Conventions  
This guidance from Tetrate explains why a proper `appProtocol` naming pattern is critical for protocol detection and routing in a service mesh.  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0602)

## Conclusion

Enforcing a standardized `appProtocol` convention on Service ports is vital for reliable traffic management in your Kubernetes and Istio environment. This Kyverno policy prevents misconfigured or missing `appProtocol` values that could lead to protocol mismatches and routing failures.
