# Instavote App - Continuous Deployment with ArgoCD

### Deploy the applications:

#### Manually  
Deploy the applications on Kubernetes with ArgoCD manually, using the manifests in `<application-name>/deployments` folder.

- or

#### Automatically  
Deploy running `$ ansible-playbook argo-gitops/deploy-instavote/deploy-instavote.yml`.


### Create Continuous Deployment Pipelines:
![CD Pipeline](cd-pipeline.png)
#### 01. Allow Jenkins to Deploy on ArgoCD
Run: `$ ansible-playbook argo-gitops/allow-jenkins/allow-jenkins.yml`  

#### 02. Create the Pipelines
Add variables as secret text, in Global Credentials:
- argocd-jenkins-deployer-token = The token produced in the previous step.
- argo-server-ip                = in the form of [IP]:[port]
- vote-app-url                  = in the form of http://[IP]:[port]
- result-app-url                = in the form of http://[IP]:[port]

Create new Multibranch Pipelines on Jenkins, with:
- Source as GitHub repo (eg. https://github.com/xvag/instavote-cd-argo.git)
- Build mode "by Jenkinsfile" with Script Path pointing to the Jenkinsfile (eg. vote/Jenkinsfile)

### Requirements:
- Working ArgoCD Setup
- Working Jenkins Setup, with Kubernetes Cloud
- Ansible with kubernetes module
- kubectl (configured with the working kubernetes cluster)
- argocd CLI (logged in to the ArgoCD server)
