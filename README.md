# openshift-gitops-kustomize
A repository for deploying Openshift clusters with ACM and Argo CD.  
All cluster lifecycle is managed by Argo CD, including Argo configuration itself.

## How to run it
```shell
until oc apply -k https://github.com/natifridman/openshift-gitops-kustomize/cluster-mgmt/bootstrap/overlays/default; do sleep 3; done
```

# Structure
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

|#|Directory Name|Description|
|---|----------------|-----------------|
| 1. | `bootstrap` | This is where openshift-gitops configurations is stored. These are the items that get the cluster/automation started. <br /><br /> `base` is where are the "common" YAML would live and `overlays` are configurations specific to the cluster. |
| 2. | `components` | This is where specific components for the GitOps Controller lives (in this case Argo CD).<br /><br />`applicationsets` is where all the ApplicationSets YAMLs live.<br /><br />Other things that can live here are RBAC, Git repo, and other Argo CD specific configurations (each in their repsective directories). |
| 3. | `core` | This is where YAML for the core functionality of the cluster live. Here is where the Kubernetes administrator will put things that is necissary for the functionality of the cluster.<br /><br />Under `gitops-controller` is where you are using Argo CD to manage itself. The `kustomization.yaml` file uses `cluster-mgmt/bootstrap/overlays/default` in it's `bases` configuration. This `core` directory gets deployed as an applicationset which can be found under `cluster-mgmt/components/applicationsets/core-components-appset.yaml`.<br /><br />To add a new "core functionality" workload, one needs to add a directory with some yaml in the `core` directory. See the `advanced-cluster-management` directory as an example.|
| 4. | `clusters` | This is where the new clusters configuration is stored. <br /><br /> To add a new workload cluster, one needs to add a directory with some yaml in the `overlays` directory. See the `blazer` directory as an example.|