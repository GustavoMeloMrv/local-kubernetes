# Add the Prometheus Helm repository:

```powershell
kubectl create namespace monitoring
```

```powershell
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```

```powershell
helm repo update
```

```powershell
kubectl create secret generic grafana-admin-credentials --from-literal=admin-user=admin --from-literal=admin-password='chucky!123' -n monitoring
```

```powershell
helm install -n monitoring prometheus prometheus-community/kube-prometheus-stack -f values.yaml
```