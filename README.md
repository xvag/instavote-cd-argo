# Instavote App - Continuous Deployment with ArgoCD

### Deploy the applications:

##### Manually  
Deploy the applications on Kubernetes with ArgoCD manually, using the manifests in `<application-name>/deployments` folder.

##### Automatically  
Deploy using Automation GitOps from `argo-gitops/deploy-instavote` folder.  
Requirements:  
- Ansible  
- kubectl (configured with the working kubernetes cluster)  
- argocd CLI (logged in to the ArgoCD server)  

Deploy with `$ ansible-playbook deploy-instavote.yml`
