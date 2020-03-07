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
        //sh 'docker images'
      }
    }
     
    stage('Run kubectl') {
          steps {
	      container('kubectl') {
	        sh "kubectl get pods"
	        sh "cat deployment-example.yaml"
	        //sh "kubectl delete -f deployment-example.yaml"
	        sh "kubectl apply -f deployment-example.yaml --dry-run=true "
	        sh "kubectl get pods"
	      }
      }
    }
  }
}