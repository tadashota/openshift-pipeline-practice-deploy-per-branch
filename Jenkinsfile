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
      script{
        openshift.withCluster(){
          openshift.apply(('-f', 'template-deploy.yaml')))
        }
      }
    }
  }

  stage('pruduction deploy'){
    when {
        branch 'master'
    }
    steps{
      echo "production deploy"
      script{
        openshift.withCluster(){
          openshift.apply(('-f', 'template-deploy.yaml')))
        }
      }
    }
  }
}
