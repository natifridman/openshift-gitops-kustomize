# openshift-gitops-kustomize

```shell
until kubectl apply -k https://github.com/natifridman/openshift-gitops-kustomize/cluster-mgmt/bootstrap/overlays/default; do sleep 3; done
```