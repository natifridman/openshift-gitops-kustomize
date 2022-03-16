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
|   |-- components
|   |   `-- applicationsets
|   |       `-- core-components-appset.yaml
|   `-- core
|       |-- acm-operator
|       |   |-- acm-multi-cluster-hub.yaml
|       |   |-- acm-subscription.yaml
|       |   `-- kustomization.yaml
|       `-- gitops-controller
|           `-- kustomization.yaml
|-- LICENSE
`-- README.md
```