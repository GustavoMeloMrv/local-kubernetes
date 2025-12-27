# Windows
```powershell
winget install Kubernetes.kind
```

# Configuring Your kind Cluster
```powershell
kind create cluster --config kind-example-config.yaml
winget install Kubernetes.kind
```

# Install Helm
https://helm.sh/docs/intro/install/
Config Windows path variables

# Ip Range
```powershell
docker network inspect -f '{{.IPAM.Config}}' kind
[{fc00:f853:ccd:e793::/64 invalid Prefix fc00:f853:ccd:e793::1 map[]} {172.18.0.0/16 invalid Prefix 172.18.0.1 map[]}]
```