# Home
[You are here](https://arslankhanali.github.io/rc-helm-charts/)

# Helm Chart Repository

- [rbac](https://github.com/arslankhanali/rc-helm-charts/tree/main/charts/rbac)
- [s2i](https://github.com/arslankhanali/rc-helm-charts/tree/main/charts/s2i)



## Usage

Install helm on your machine using the [official docs](https://helm.sh/docs/intro/install/)

```shell
helm repo add arslankhanali https://arslankhanali.github.io/rc-helm-charts/
```
```shell
helm repo update
```
```shell
helm search repo arslankhanali
```
```shell
helm install rbac arslankhanali/rbac --set <value-To-Override-In-Values.yaml>=<your-Value>
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
  repoURL: https://arslankhanali.github.io/rc-helm-charts/
  chart: s2i
  targetRevision: 0.0.2
  overrides:
  - name: appName
    value: infapp
  - name: namespace
    value: infapp
  - name: consoleLink.text
    value: 'infapp'
  - name: consoleLink.section
    value: Gradio App 1
  - name: environment.env[0].name
    value: INFERENCE_ENDPOINT
  - name: environment.env[0].value
    value: http://modelmesh-serving.credit-fraud-model:8008/v2/models/credit-card-fraud/infer
  - name: environment.env[1].name
    value: 'env-variable-shouldnot-have-a-space'
  - name: environment.env[1].value
    value: testing adding another env
```

### In command line
``` sh 
helm install s2i https://arslankhanali.github.io/my-helm-charts/s2i --set appName=infapp
```
