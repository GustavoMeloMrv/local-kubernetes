# Add the MetalLB Helm repository:

```powershell
kubectl create namespace metallb-system
```

```powershell
helm repo add metallb https://metallb.github.io/metallb
```

```powershell
helm repo update
```

```powershell
helm install metallb metallb/metallb --namespace metallb-system --create-namespace
```

```powershell
kubectl apply -f configuration.yaml
```