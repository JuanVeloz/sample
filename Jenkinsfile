pipeline {
  agent any
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