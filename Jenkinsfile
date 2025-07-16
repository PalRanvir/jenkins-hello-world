pipeline {
  agent any
  stages {
    stage('Echo Version') {
      steps {
        sh 'echo Print Maven Version'
        sh 'mvn -version'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean install -DskipTests'
        archiveArtifacts 'target/hello-demo-*.jar'
      }
    }

    stage('Unit Test') {
      steps {
        sh 'mvn test'
        junit(testResults: 'target/surefire-reports/TEST-*.xml', keepProperties: true, keepTestNames: true)
      }
    }
    
    stage('Containerization') {
      steps {
        sh 'echo Docker Build Image'
        sh 'echo Docker Tag Image'
        sh 'echo Docker Push Image'  
      }
    }
    
    stage('Kubernetes Deployment') {
      steps {
        sh 'echo Deploy to Kubernetes using AgroCD'
      }
    }
    
    stage('Integration Testing') {
      steps {
        sh 'sleep 10s'
        sh 'echo Testing using cURL command'
      }
    }

  }
  tools {
    maven 'M398'
  }
}
