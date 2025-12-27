## Windows

# The easiest way to get k3d running on Windows is with Chocolatey:
https://chocolatey.org/install

# Open a new administrative instance and run the following to install k3d and a couple other useful tools:
```powershell
choco install k3d -y
choco install jq -y
choco install yq -y
choco install kubernetes-helm -y
```

# And now let’s configure tab completion for k3d:

###### Create user profile file if it doesn't exist
```powershell
if ( -not ( Test-Path $Profile ) ) { New-Item -Path $Profile -Type File -Force }
```
    
###### Append the k3d completion to the end of the user profile
```powershell
k3d completion powershell | Out-File -Append $Profile
```

# Create a new multi-node cluster
```powershell
k3d cluster create traefik `
  --port 80:80@loadbalancer `
  --port 443:443@loadbalancer `
  --port 8000:8000@loadbalancer `
  --k3s-arg "--disable=traefik@server:0"
```