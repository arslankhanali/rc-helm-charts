# Home
[You are here](https://arslankhanali.github.io/my-helm-charts/)

# Helm Chart Repository

- [rbac](https://github.com/arslankhanali/my-helm-charts/tree/main/charts/rbac)
- [s2i](https://github.com/arslankhanali/my-helm-charts/tree/main/charts/s2i)



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

### In validated pattern
```yml
infapp:
  name: infapp
  namespace: infapp
  project: infapp
  repoURL: https://arslankhanali.github.io/my-helm-charts/
  chart: s2i
  targetRevision: 0.0.1 
  overrides:
  - name: appName
    value: infapp
  - name: namespace
    value: infapp
  - name: consoleLink.text
    value: infapp
```

### In command line
``` sh 
helm install s2iChart https://arslankhanali.github.io/my-helm-charts/s2i --set appName=infapp
```
