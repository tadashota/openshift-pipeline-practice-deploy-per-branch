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
        sh '''
        oc apply -f template-deploy-stag.yaml'''
      }
    }
  }
}
