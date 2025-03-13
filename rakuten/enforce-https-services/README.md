# Enforce HTTPS Services Policy

## Overview

The `enforce-https-services.yaml` file defines a Kyverno ClusterPolicy that ensures all Kubernetes Services utilize only HTTPS or TCP protocols. This policy is crucial for maintaining security by preventing the use of HTTP-based ports.


## Description

This policy audits and denies any Kubernetes Service that attempts to use HTTP-based ports, specifically:
- Port 80
- Port 8080
- Port 8000
- Port 8888
- Port 3000

The policy validates the `spec.ports` of the Service and ensures that only TCP or HTTPS protocols are allowed.

## Usage

To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML file using the following command:
```bash
kubectl apply -f enforce-https-services.yaml
```

## Conclusion

Implementing the Enforce HTTPS Services Policy is a vital step in securing your Kubernetes environment. By ensuring that only secure protocols are used, you can protect your applications from potential vulnerabilities associated with HTTP traffic. Regularly review and update your policies to adapt to evolving security standards and practices.

