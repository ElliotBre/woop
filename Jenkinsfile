pipeline {
    agent any
    environment{
        DOCKER_LOGIN = credentials('DOCKER_LOGIN')
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
                 sh 'docker login -u ${DOCKER_LOGIN_USR} -p ${DOCKER_LOGIN_PSW}'
                 sh 'sudo docker push mmbatteries/veryCoolApp:latest'
                
                 sh 'echo success'


            }
 
        }
}
