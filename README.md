# Instavote App - Continuous Deployment with ArgoCD

### Deploy the applications:

#### Manually  
Deploy the applications on Kubernetes with ArgoCD manually, using the manifests in `<application-name>/deployments` folder.

- or -

#### Automatically  
Deploy running `$ ansible-playbook argo-gitops/deploy-instavote/deploy-instavote.yml`.

##### Requirements:
- Ansible
- kubectl (configured with the working kubernetes cluster)
- argocd CLI (logged in to the ArgoCD server)

### Create Continuous Deployment Pipelines
#### Allow Jenkins to Deploy on ArgoCD
Run `$ ansible-playbook argo-gitops/allow-jenkins/allow-jenkins.yml`
##### Requirements:
-
