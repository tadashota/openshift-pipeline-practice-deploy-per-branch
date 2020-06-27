#!groovy
def ns_stag = "user1-app-stag"
def ns_prod = "user1-app-prod"

pipeline {
  agent {
    kubernetes {
      cloud 'openshift'
      yamlFile 'jenkins-agent-pod.yaml'
    }
  }

  stage('staging deploy'){
    when {
        branch 'staging'
    }
    steps{
      echo "staging deploy"
      sh 'oc apply -f template-deploy-stag.yaml'
      }
    }
  }

  stage('pruduction deploy'){
    when {
        branch 'master'
    }
    steps{
      echo "production deploy"
      sh 'oc apply -f template-deploy-prod.yaml'
      }
    }
  }
}
