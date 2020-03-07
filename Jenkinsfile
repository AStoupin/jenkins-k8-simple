pipeline {
  agent {
    kubernetes {
      yaml 'pod-example.yaml'
    }
  }
  stages {
    stage('Run maven') {
      steps {
      
        container('maven') {
          sh 'mvn -version'
        }
        container('busybox') {
          sh '/bin/busybox'
        }
      }
    }
  }
}