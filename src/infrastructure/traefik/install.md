# Add the Traefik Helm repository:
```powershell
kubectl create namespace traefik
```

```powershell
helm repo add traefik https://traefik.github.io/charts
```

```powershell
helm repo update
```

###### Option 1
```powershell
helm install traefik traefik/traefik -f values.yaml --wait
```

###### Option 2
```powershell
helm install traefik traefik/traefik --wait `
  --set ingressRoute.dashboard.enabled=true `
  --set ingressRoute.dashboard.matchRule='Host(`traefik.localhost`)' `
  --set ingressRoute.dashboard.entryPoints={web} `
  --set providers.kubernetesGateway.enabled=true `
  --set gateway.listeners.web.namespacePolicy.from=All
```

```powershell
kubectl describe GatewayClass traefik
```

###### To use the Gateway API - Install the Gateway API CRDs in your cluster:
```powershell
kubectl apply -f https://github.com/kubernetes-sigs/gateway-api/releases/download/v1.2.1/standard-install.yaml
```

http://traefik.localhost/dashboard/