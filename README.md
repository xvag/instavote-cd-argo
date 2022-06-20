# Instavote App - Continuous Deployment with ArgoCD

## Deploy the applications

01. Manually
Deploy the applications on Kubernetes with ArgoCD manually, using the manifests in `<application-name>/deployments` folder.

02. Automatically
Deploy using Automation GitOps from `argo-gitops/deploy-instavote` folder.
- Requirements:
01. kubectl (configured with the working kubernetes cluster)
02. argocd CLI (logged in to the ArgoCD server)