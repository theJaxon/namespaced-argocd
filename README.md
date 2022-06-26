# namespaced-argocd
An attempt to automate namespaced argocd deployment

### Introduction
- Before proceeding with reading anything just note that, while the title is correct and this is a namespaced argocd installation, there's only one aspect where cluster wide permissions are needed and that's argocd CRDs as these are non namespaced and require a cluster admin to install them, other than that anything else is namespaced.
- [CRDs include](https://github.com/argoproj/argo-cd/tree/master/manifests/crds)
  1. applications.argoproj.io
  2. appprojects.argoproj.io
- Optional CRD that can be handy is [ApplicationSet CRD](https://github.com/argoproj/argo-cd/blob/master/manifests/crds/applicationset-crd.yaml)
- namespaced argocd is benefecial in situations where the deployment is happening on a multi-tenant kubernetes cluster where you don't play the role of a cluster admin so the idea is to deploy argocd with limited privileges
- For this you can refer to this really great article by [Andrew Block](https://blog.andyserver.com/2020/12/argocd-namespace-isolation/) to get an idea of what initial implementation should look like
- Till the blog is back online you can [view an archived version](https://web.archive.org/web/20201221142008/https://blog.andyserver.com/2020/12/argocd-namespace-isolation/) 
---

### How to use 

```bash
# Clone the repository 
git clone https://github.com/theJaxon/namespaced-argocd.git

cd  namespaced-argocd

# Edit the script and specify the namespaces needed for your use case 
# Main namespace is where argocd componenets should be deployed
# Target namespaces is a comma separated list of namespaces that argocd will be managing
vi namespaced_argo.sh

# Make the script executable 
chmod +x namespaced_argo.sh

# Run the script 
./namespaced_argo.sh
```