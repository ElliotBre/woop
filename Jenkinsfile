pipeline {
    agent any
    environment{
        DOCKERHUB_CREDENTIALS = credentials('DOCKER_LOGIN')
    }
    stages{
        stage('BUILD'){
              steps {
                     sh  "docker compose up -d"  
                     }
                   }
        stage('TEST'){
             steps {
                    sh 'python3 --version'
                    sh 'docker ps -a'
                    sh "curl localhost:80"
                   }
                 }
               }
        post {
            always {
                 sh "docker compose down -v"
            }
            success {
                 sh 'echo $DOCKER_LOGIN_PSW | sudo docker login - u $DOCKER_LOGIN_USR --password-stdin'
                 sh 'sudo docker push ${DOCKER_LOGIN_USR}/app:latest'
                 sh 'docker logout'


            }
 
        }
}
