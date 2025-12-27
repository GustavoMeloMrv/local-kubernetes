# Commands
```powershell
kubectl create namespace argocd
```

```powershell
helm repo add argo https://argoproj.github.io/argo-helm
```

```powershell
helm repo update
```

###### Add the annotation for ssl passthrough: "server.insecure=true"
https://argo-cd.readthedocs.io/en/stable/operator-manual/ingress/#option-1-ssl-passthrough

###### Ingress is disabled because we are using Traefik: "server.ingress.enabled=false"

```powershell
helm install argocd argo/argo-cd --namespace argocd `
    --set server.ingress.enabled=false `
    --set server.insecure=true `
    --create-namespace
```

# Change ArgoCD Service to LoadBalancer (if needed)
```powershell
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
```

# Configure Argo CD for HTTP Access 
```powershell
kubectl edit configmaps argocd-cmd-params-cm -n argocd
```

# ArgoCD UI
###### In order to access the server UI you have the following options:
```powershell
kubectl port-forward service/argocd-server -n argocd 8080:443
```
###### and then open the browser on http://localhost:8080 and accept the certificate

###### After reaching the UI the first time you can login with username: admin and the random password generated during the installation. You can find the password by running:
readthedocs.io/en/stable/operator-manual/ingress/#option-2-multiple-ingress-objects-and-hosts

```powershell
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

    base64: ZGNVa1J3MERIYVFQR0hhYQ==
    password decode: dcUkRw0DHaQPGHaa
    user: admin