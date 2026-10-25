pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
     
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
                sh 'ls -lh target/*.jar'
            }
        }
      }

      post {
          success {
              archiveArtifacts artifacts: 'target/*.jar'
          }
      }
}
