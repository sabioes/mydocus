# Kubernetes

## Commands
Force delete a namespace stuck in terminating state:
```bash
kubectl get namespace <NAMESPACE> -o json   | jq '.spec.finalizers = []'   | kubectl replace --raw "/api/v1/namespaces/<NAMESPACE>/finalize" -f - 
```

## Explicit Multi-config file for kubectl and permanent KUBECONFIG variable
```bash
# Set KUBECONFIG from ~/.kube ignoring folders, if permanent export it in .bashrc or .zshrc
export KUBECONFIG=$(find ~/.kube -maxdepth 1 -type f -printf "%p:" | sed 's/:$//')
```