# Instavote App - Continuous Deployment with ArgoCD

## Deploy the applications

01. Deploy the applications on Kubernetes with ArgoCD manually, using the manifests in `<application-name>/deployments` folder.

or

02. Deploy using Automation GitOps from `argo-gitops/deploy-instavote` folder.
##### Requirements:
- kubectl (configured with the working kubernetes cluster)
- argocd CLI (logged in to the ArgoCD server)
