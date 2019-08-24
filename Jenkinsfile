pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3001:3000'
    }

  }
  stages {
    stage('Install') {
      steps {
        sh 'npm install'
      }
    }
    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }
    stage('Test') {
      steps {
        sh 'npm test'
        emailext(subject: 'Aprobar', body: 'Por favor aprueba', attachLog: true, to: 'Juan')
      }
    }
    stage('Approve') {
      steps {
        input(message: '¿Se aprueba?', submitter: 'Juan')
      }
    }
    stage('Deploy') {
      steps {
        echo 'Succesful'
      }
    }
  }
}
