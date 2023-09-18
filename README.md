# Home
[You are here](https://arslankhanali.github.io/my-helm-charts/)

# Helm Chart Repository

[rbac](https://github.com/arslankhanali/my-helm-charts/tree/main/charts/rbac)



## Usage

Install helm on your machine using the [official docs](https://helm.sh/docs/intro/install/)

```shell
helm repo add arslankhanali https://arslankhanali.github.io/my-helm-charts/
```
```shell
helm repo update
```
```shell
helm search repo arslankhanali
```
```shell
helm install rbac arslankhanali/rbac
```

```shell
helm uninstall rbac
```