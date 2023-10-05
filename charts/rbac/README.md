# Usage

### In Chart.yaml
``` yml
dependencies:
- name: rbac
  version: 0.0.5
  #repository: "https://arslankhanali.github.io/rc-helm-charts"
  repository: "https://day0hero.github.io/helm-charts"
  #repository: "https://charts.validatedpatterns.io/"
```
### In values.yaml
``` yml
rbac:
  name: lvms
  namespace: openshift-storage
  roles:
    - createRole: true
      resources:
        - storageclasses
      scope:
        cluster: true
      apiGroups:
        - "storage.k8s.io"
      verbs:
        - "get"
        - "list"
        - "patch"
        - "update"
```

### rbac-chart
Helm Chart to define RBAC for application deployments.

Using the chart defaults an rbac will be created (clusterRole, clusterRoleBinding and ServiceAccount)
named `rbac` in the `default` namespace. This role has read (get, list, watch) on all resources. 

| Parameter | Default Value |
| --------- | ------------- |
| name | rbac |
| namespace | default |
| createRole | true |
| scope.cluster | true |
| resources | * |
| verbs | get, list, watch |
| createBinding | true |
| scope.cluster | true |
| subjects | ServiceAccount |
| apiGroup | "" |