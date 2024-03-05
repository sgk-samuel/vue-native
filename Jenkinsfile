pipeline {
  agent any

  stages {
    stage('Test') {
      steps {
        sh "npm install"
        sh "npm run test:unit"
        sh "npm run test:e2e"
      }
    }
    
    stage("Build") {
      steps {
        sh "npm run build:prod"
      }

      post {
        always{
          echo "========always========"
        }
        success{
          echo "========A executed successfully========"
        }
        failure{
          echo "========A execution failed========"
        }
      }
    }

    stage("Deploy") {
      steps {
        sh "chmod +x ./scripts/**/*.sh"
        sh "./scripts/deploy.sh"
        input "continue ? "

      }
    }
  }

  post{
    always{
      echo "========always========"
    }
    success{
      echo "========A executed successfully========"
    }
    failure{
      echo "========A execution failed========"
    }
  }
}