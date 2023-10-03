    
    ### Usage
    ####
    helm install  https://arslankhanali.github.io/my-helm-charts/s2i --set appName=infapp

    ####
    infapp:
      name: infapp
      namespace: infapp
      project: infapp
      repoURL: https://arslankhanali.github.io/my-helm-charts/
      chart: s2i
      targetRevision: 0.0.1 # 0.6.* # using "*" gave me an error
      overrides:
      - name: appName
        value: infapp
      - name: namespace
        value: infapp
      - name: consoleLink.text
        value: infapp

