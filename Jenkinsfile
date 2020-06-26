pipeline {
  agent {
    kubernetes {
      cloud 'openshift'
      yamlFile 'jenkins-agent-pod.yaml'
    }
  }

  stages {
    stage('deploy') {
      steps {
      echo "staging deploy"
      script{
        openshift.withCluster(){
        openshift.apply(('-f', 'template-deploy-stag.yaml')))
        }
      }
    }
  }
}
