# Namespace Protection Policy

## Overview
The Namespace Protection policy is designed to prevent modifications to Kubernetes namespaces that are labeled as frozen. This policy is particularly useful in scenarios where certain namespaces need to be protected from accidental updates or deletions, ensuring that critical resources remain intact.

## Features
- **Freeze Protection**: Blocks updates and deletions on any namespace labeled with `freeze=true`.
- **Namespace Deletion Prevention**: Specifically prevents the deletion of namespaces that are marked as frozen.


## Usage
You can apply the policy using the following command:
```bash
kubectl apply -f enforce-https-services.yaml
```

For example, to freeze a namespace, you can use the following command:
```bash
kubectl label namespace <namespace-name> freeze=true
```

Once labeled, any attempts to update or delete the namespace will be denied with a corresponding message.
