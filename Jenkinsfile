pipeline {
  agent {
    kubernetes {
      yamlFile 'pod-example.yaml'
    }
  }
  stages {
    stage('Run maven') {
      steps {
      
        container('maven') {
          sh 'mvn -version'
          sh 'kubectl get po'
        }
        container('busybox') {
          sh '/bin/busybox'
        }
      }
    }
  }
}