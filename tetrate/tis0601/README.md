# Validate Service Port Names (Regex)

## Overview

The `validate-service-port-names-regex` policy is a Kyverno ClusterPolicy designed to enforce a consistent naming convention for Kubernetes Service ports. It uses a regular expression to ensure each port name follows the `protocol[-suffix]` format, where `protocol` is one of:

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

By validating port names, this policy helps Istio and other service mesh components correctly identify and route traffic based on the declared protocol.

## Usage

To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and run:

```bash
kubectl apply -f check-portname-conventions.yaml
```

## Web Reference

For more details, see:  
TIS0601 – Service Port Name Conventions  
This guidance from Tetrate outlines the importance of using proper port naming patterns to avoid routing misconfigurations in a service mesh.  
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0601)

## Conclusion

Enforcing a standardized Service port naming convention is crucial for reliable traffic management in your Kubernetes and Istio environment. This Kyverno policy prevents misnamed ports that could lead to protocol mismatches and routing failures.
