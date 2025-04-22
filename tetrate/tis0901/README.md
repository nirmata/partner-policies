# Ensure Non-Empty Providers in Telemetry Spec
## Overview
The `check-telemetry-non-empty-provider` policy is a Kyverno ClusterPolicy designed to ensure that Telemetry resources are properly configured with non-empty providers for both access logging and metrics. This policy enforces that each Telemetry resource includes at least one provider with a non-empty name in both the accessLogging and metrics sections.

The policy specifically:
- Validates that Telemetry resources have non-empty providers for access logging
- Ensures Telemetry resources have non-empty providers for metrics
- Prevents creation of Telemetry resources with empty provider configurations
- Helps maintain proper observability configurations

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f check-telemetry-non-empty-provider.yaml
```

## Web Reference
For more details, see:
TIS0901 - Telemetry Has Empty Provider Configuration
This guidance from Tetrate outlines the importance of properly configuring providers in Telemetry resources and explains the potential issues that can arise from empty provider configurations.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS0901)

## Conclusion
Proper configuration of Telemetry providers is crucial for maintaining effective observability in the service mesh. This Kyverno policy ensures that all Telemetry resources have properly configured providers for both access logging and metrics, preventing potential observability gaps and maintaining comprehensive monitoring capabilities.
