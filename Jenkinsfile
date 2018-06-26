pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo "BUILD"
        sh 'docker build -t app:test .'
      }      
    }

    stage('Test') {
      steps {
        echo "TEST"
        sh "docker run --rm --name app -id -p 80:80 app:test"
        sh "/bin/nc -vz localhost 80"
      } post{
          alwayas{
            sh "docker container stop app"
          }
      }

    }
    stage('Deploy') {
      steps {
        echo "DEPLOY"
        //sh "docker tag app:test app:stable"
        
    }

      }      


  }
}