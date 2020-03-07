pipeline {
 /* agent {
    kubernetes {
      yamlFile 'deployment-example.yaml'
    }
  }*/
  stages {
    /*stage('Run maven') {
      steps {
      
        container('maven') {
          sh 'mvn -version'
        }
        container('busybox') {
          sh '/bin/busybox'
        }

          sh 'kubectl get po'
      }
    }*/
    
    stage('Deployument') {
      steps {
               sh "kubectl cluster-info"
      }
    }
  }
}