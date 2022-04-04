# openshift-gitops-kustomize

```shell
until kubectl apply -k https://github.com/natifridman/openshift-gitops-kustomize/cluster-mgmt/bootstrap/overlays/default; do sleep 3; done
```

```shell
|-- cluster-mgmt
|   |-- bootstrap
|   |   |-- base
|   |   |   |-- kustomization.yaml
|   |   |   `-- openshift-gitops-subscription.yaml
|   |   `-- overlays
|   |       `-- default
|   |           |-- kustomization.yaml
|   |           |-- openshift-gitops-argocd.yaml
|   |           `-- openshift-gitops-rbac-policy.yaml
|   |-- clusters
|   |   |-- base
|   |   `-- overlays
|   |-- components
|   |   `-- applicationsets
|   |       |-- clusters-appset.yaml
|   |       |-- core-components-appset.yaml
|   |       `-- kustomization.yaml
|   `-- core
|       |-- advanced-cluster-management
|       |   `-- kustomization.yaml
|       |-- gitops-controller
|       |   `-- kustomization.yaml
|       `-- sealed-secrets
|           |-- kustomization.yaml
|           `-- namespace.yaml
|-- LICENSE
`-- README.md
```