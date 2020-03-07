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
        }
        container('busybox') {
          sh '/bin/busybox'
        }

      }
    }
     
    stage('Run kubectl') {
      container('kubectl') {
        sh "kubectl get pods"
      }
    }
  }
}