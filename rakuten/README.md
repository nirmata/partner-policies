[Robin Cloud Native Platform (CNP)](https://docs.robin.io/platform/5.4.3/overview.html) is a CNCF compliant Kubernetes-based platform that automates the deployment, scaling and lifecycle management of Data and Network intensive applications. However, without automated guardrails, storage misconfigurations, security vulnerabilities, and compliance gaps can arise. By integrating Nirmata’s policy-driven governance capabilities with Robin CNP, we aim to automate compliance, simplify audits, and prevent misconfigurations—delivering scalable, enterprise-ready storage management.

### Deploy policies
```sh
kubectl apply -k .
```

### View policies
```sh
kubectl get cpol
```

### View policy reports
```sh
kubectl get polr -A
```
