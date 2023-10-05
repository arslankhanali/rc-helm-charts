    
### Usage
####

```shell
helm repo add rc-helm-charts https://arslankhanali.github.io/rc-helm-charts/
helm repo update
helm search repo rc-helm-charts
helm install s2i rc-helm-charts/s2i --set appName=infapp \
                                    --set   namespace=infapp \
                                    --set   uri=https://github.com/arslankhanali/credit-fraud-detection-demo \
                                    --set   contextDir=application \
                                    --set   originalimage=python:3.10.4 \
                                    --set   port=8080 \
                                    --set   protocol=TCP \
```


####
``` yml
    infapp:
      name: infapp
      namespace: infapp
      project: infapp
      repoURL: https://arslankhanali.github.io/rc-helm-charts/
      chart: s2i
      targetRevision: 0.0.3
      overrides:
      #Basic
      - name: appName
        value: infapp
      - name: namespace
        value: infapp
      - name: uri
        value: https://github.com/arslankhanali/credit-fraud-detection-demo
      - name: contextDir
        value: application
      - name: originalimage
        value: python:3.10.4
      # Ports for svc and route
      - name: port
        value: 8080
      - name: protocol
        value: TCP
      # env variables to add to deployment
      - name: environment.enable
        value: true
      - name: environment.env[0].name
        value: INFERENCE_ENDPOINT
      - name: environment.env[0].value
        value: http://modelmesh-serving.credit-fraud-model:8008/v2/models/credit-card-fraud/infer
      - name: environment.env[1].name
        value: 'env-variable-shouldnot-have-a-space'
      - name: environment.env[1].value
        value: testing adding another env
      # ConsoleLink if required
      - name: consoleLink.createLink
        value: true
      - name: consoleLink.section
        value: Gradio App 1
      - name: consoleLink.text
        value: 'infapp'
      - name: consoleLink.location
        value: ApplicationMenu
      - name: consoleLink.base64image
        values: data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAARgA
```
