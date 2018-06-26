pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t app .'
      }      
    }

    stage('Test') {
      steps {
        sh "/bin/nc -vz localhost 22"
        //sh "/bin/nc -vz localhost 80"
      }      
    }
    stage('Deploy') {
      steps {
        sh "docker tag app:test app:stable"
        echo 'DEPLOY'
    }
      }      


  }
}