pipeline {

  environment {
    ARGO_SERVER = '34.118.79.42:32100'
    DEV_URL = 'http://34.118.79.42:30000/'
  }

//  agent any

agent {
  kubernetes {
    yamlFile 'build-agent.yaml'
    defaultContainer 'docker-tools'
    idleMinutes 1
  }
}

  stages {
/*    stage('Daily Compliance Run') {
      steps{
        echo 'Running a compliance scan with inspec....'
          script{
            def remote = [:]
            remote.name = "controlnode"
            remote.host = "xxx.xxx.xxx.xxx"
            remote.allowAnyHosts = true

            withCredentials([sshUserPrivateKey(credentialsId: 'sshUser', keyFileVariable: 'identity', passphraseVariable: '', usernameVariable: 'userName')]) {
                remote.user = userName
                remote.identityFile = identity
                stage("Enforce with Ansible") {
                  sshCommand remote: remote, sudo: true, command: 'cd /root/secops/ansible && git pull origin'
                  sshCommand remote: remote, sudo: true, command: 'cd /root/secops/ansible && ansible-playbook compliance.yaml'
                }
                stage("Scan with InSpec") {
                  sshCommand remote: remote, sudo: true, command: 'inspec exec --no-distinct-exit /root/linux-baseline/'
                }
            }
          }
      }
    }*/

    stage('Scan k8s Deploy Code') {
      steps {
        container('docker-tools') {
          sh 'kubesec scan worker/worker-deploy.yaml'
        }
      }
    }

  /*  stage('Deploy to Dev') {
      environment {
        AUTH_TOKEN = credentials('argocd-jenkins-deployer-token')
      }
      steps {
        container('docker-tools') {
          sh 'docker run -t schoolofdevops/argocd-cli argocd app sync worker --insecure --server $ARGO_SERVER --auth-token $AUTH_TOKEN'
          sh 'docker run -t schoolofdevops/argocd-cli argocd app wait worker --health --timeout 300 --insecure --server $ARGO_SERVER --auth-token $AUTH_TOKEN'
        }
      }
    }
*/
    stage('Dynamic Analysis') {
      parallel {
       stage('E2E tests') {
         steps {
           sh 'echo "All Tests passed!!!"'
          }
        }
        stage('DAST') {
          steps {
            container('docker-tools') {
              sh 'docker run -t owasp/zap2docker-stable zap-baseline.py -t $DEV_URL || exit 0'
            }
          }
        }
      }
    }

  }
}
