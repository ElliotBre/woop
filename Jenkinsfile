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
            success {
                 sh 'docker login -u ${DOCKER_LOGIN_USR} -p ${DOCKER_LOGIN_PSW}'
                 sh 'docker compose push'
                  
                 sh 'echo success'


            }
            always {
                 sh 'docker compose down -v'
            }
 
        }
}
