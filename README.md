# PHPIPAM Helm chart

## Pre-requiste
* Docker
* Kubernetes

## How To Use

1. Install Kubernetes Cluster with Kind

(This step is optional, monikube or k3s could be used to runing Kubernetes Locally)

(Install Kind)[https://kind.sigs.k8s.io/docs/user/quick-start/#installing-from-release-binaries]

### Linux

```bash
# For AMD64 / x86_64
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64
# For ARM64
[ $(uname -m) = aarch64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-arm64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```
### Windows

```powershell
curl.exe -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.20.0/kind-windows-amd64
Move-Item .\kind-windows-amd64.exe c:\some-dir-in-your-PATH\kind.exe
```

2. Create Kubernetes Cluster

```bash
kind create cluster
```
3. Install Mysql

```bash
kubectl apply -f https://gist.githubusercontent.com/leandromoreirati/b5be442d3fc1110ef0056fdd88d67bcd/raw/b394dfa16d9371b2ef94d6f44ce4641c47a7eb6b/mysql.yaml
```
4. Install PHPIPAN

```bash
helm -n phpipam upgrade --install --create-namespace phpipam -f values.yaml charts/
```


