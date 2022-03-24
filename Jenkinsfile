pipeline {

//  agent any

agent {
  kubernetes {
    yamlFile 'build-agent.yaml'
    defaultContainer 'docker-tools'
    idleMinutes 1
  }
}

/*  stages {
    stage('Daily Compliance Run') {
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
    }
  }*/

  stage('Scan k8s Deploy Code') {
    steps {
      container('docker-tools') {
        sh 'kubesec scan worker/worker-deploy.yaml'
      }
    }
  }
}
