pipeline {
  agent any

  stages {

    stage('Build Backend') {
      steps {
        sh 'docker build -t backend ./backend'
      }
    }

    stage('Build Frontend') {
      steps {
        sh 'docker build -t frontend ./frontend'
      }
    }

    stage('Run Containers') {
      steps {
        sh 'docker rm -f backend-container || true'
        sh 'docker rm -f frontend-container || true'

        sh 'docker run -d -p 5000:5000 --name backend-container backend'
        sh 'docker run -d -p 5173:5173 --name frontend-container frontend'
      }
    }

  }
}