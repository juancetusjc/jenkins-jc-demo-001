pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo "BUILD"
        sh 'docker build -t app:test .'
        //sh 'docker build -t app .'
      }      
    }

    stage('Test') {
      steps {
        echo "TEST"
        sh "docker run -d --name app app:test"
        //sh "docker run --rm --name app -id -p 80:80 app:test"
        //sh "docker run -d --name app -id -p 80:80 app:test"
        //sh "docker run -d app" 
        //sh "/bin/nc -vz localhost 80"
        //sh "nc -vz localhost 80"
      }
      post{
        always{
            sh "docker stop app"
          }
      }

    }
    stage('Deploy') {
      steps {
        echo "DEPLOY"
        withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'pwd', usernameVariable: 'juancetu')]) {
          sh "docker tag app juancetu/app:stable"
          sh "docker push app juancetu/app:stable"
        }

        
        
    }

      }      


  }
}