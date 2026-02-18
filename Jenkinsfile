pipeline {
  agent any
  tools {
    maven 'Maven'   // only works if Maven is configured in Jenkins Tools
  }
  stages {
    stage('Checkout') {
      steps { checkout scm }
    }
    stage('Build') {
      steps { bat 'mvn -B -DskipTests package' }
    }
    stage('Test') {
      steps { bat 'mvn -B test' }
      post {
        always { junit '**/target/surefire-reports/*.xml' }
      }
    }
  }
}
