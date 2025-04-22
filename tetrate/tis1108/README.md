# Validate JWT Claim Based Routing
## Overview
The `validate-jwt-claim-routing` policy is a Kyverno ClusterPolicy designed to ensure secure JWT claim-based routing in VirtualServices. This policy validates that when a VirtualService uses JWT claims for routing decisions, there is at least one corresponding RequestAuthentication resource in the same namespace to validate those JWT claims, preventing potential security vulnerabilities.

The policy specifically:
- Detects VirtualServices using JWT claim-based routing in their match conditions
- Checks for the presence of RequestAuthentication resources in the same namespace
- Prevents creation of VirtualServices with JWT routing without proper JWT validation
- Identifies JWT-related headers in routing rules (including both 'jwt' and 'x-jwt' prefixes)

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f validate-jwt-claim-routing.yaml
```

## Web Reference
For more details, see:
TIS1108 - VirtualService Uses JWT Claims Without RequestAuthentication
This guidance from Tetrate outlines the security risks of using JWT claim-based routing without proper JWT validation and the importance of having corresponding RequestAuthentication resources.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1108)

## Conclusion
Secure JWT claim-based routing is crucial for maintaining a secure service mesh. This Kyverno policy ensures that all VirtualServices using JWT claims for routing decisions have proper JWT validation in place through RequestAuthentication resources, preventing potential security vulnerabilities and unauthorized access.
