# Home
[You are here](https://arslankhanali.github.io/rc-helm-charts/)

# Helm Chart Repository

- [rbac](https://github.com/arslankhanali/rc-helm-charts/tree/main/charts/rbac)
- [s2i](https://github.com/arslankhanali/rc-helm-charts/tree/main/charts/s2i)



## Usage

Install helm on your machine using the [official docs](https://helm.sh/docs/intro/install/)

```shell
helm repo add rc-helm-charts https://arslankhanali.github.io/rc-helm-charts/
helm repo update
helm search repo rc-helm-charts

helm install rbac-1 rc-helm-charts/rbac

helm list 

helm uninstall rbac-1
```

## s2i chart example
#### 1 s2i example : cmd line
``` sh
helm repo add rc-helm-charts https://arslankhanali.github.io/rc-helm-charts/
helm repo update
helm install s2i-guise rc-helm-charts/s2i --set   appName=infapp3 \
                                    --set   namespace=credit-fraud-model \
                                    --set   uri=https://github.com/arslankhanali/GuiseAI-Openshift \
                                    --set   contextDir=. \
                                    --set   originalimage=docker.io/openvino/ubuntu20_runtime \
                                    --set   port=30000 \
                                    --set   protocol=TCP
```

#### 2 s2i example : validated pattern
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
