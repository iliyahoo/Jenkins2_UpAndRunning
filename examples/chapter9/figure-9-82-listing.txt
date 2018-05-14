pipeline {
  agent {
    node {
      label 'worker_node1'
    }
    
  }
  stages {
    stage('Source') {
      steps {
        git 'https://github.com/explore-jenkins/blue-ocean-demo.git'
      }
    }
    stage('Build') {
      steps {
        sh '${tool \'gradle32\'}/bin/gradle build'
      }
    }
  }
  environment {
    COMPLETED_MSG = 'Build done!'
  }
}