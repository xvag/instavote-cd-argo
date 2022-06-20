# Instavote App - Continuous Deployment with ArgoCD

### Deploy the applications:

##### Manually  
Deploy the applications on Kubernetes with ArgoCD manually, using the manifests in `<application-name>/deployments` folder.

##### Automatically  
Deploy running `$ ansible-playbook argo-gitops/deploy-instavote/deploy-instavote.yml`.

Requirements:
- Ansible
- kubectl (configured with the working kubernetes cluster)
- argocd CLI (logged in to the ArgoCD server)
