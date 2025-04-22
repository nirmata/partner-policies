# Ensure Workloads Have Authorization Policies
## Overview
The `ensure-deployment-has-authorization-policy` policy is a Kyverno ClusterPolicy designed to enforce that all Kubernetes Deployments are covered by at least one AuthorizationPolicy with matching labels. This policy ensures that workloads cannot be deployed without proper access controls in place, enhancing the security posture of your service mesh.

The policy specifically:
- Validates that each Deployment has at least one matching AuthorizationPolicy
- Uses the `app` label to match Deployments with their corresponding AuthorizationPolicies
- Prevents deployment of workloads without proper authorization controls
- Provides detailed debug information when validation fails

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f ensure-deployment-has-authorization-policy.yaml
```

## Web Reference
For more details, see:
TIS1301 - Workload Missing Authorization Policy
This guidance from Tetrate outlines the importance of enforcing authorization policies for workloads and the security risks associated with deploying workloads without proper access controls.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1301)

## Conclusion
Enforcing authorization policies for workloads is crucial for maintaining a secure service mesh. This Kyverno policy ensures that all Deployments have proper access controls in place, preventing potential security vulnerabilities and unauthorized access to services.
