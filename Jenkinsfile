pipeline {
    agent any
    stages{
        stage('BUILD'){
              steps {
                     sh  "docker compose up -d"  
                     }
                   }
        stage('TEST'){
             steps {
                    sh 'python3 --version'
                    sh 'nginx --version'
                    sh "curl localhost:80"
                   }
                 }
               }
        post {
            always {
                 sh "docker-compose down -v"
            }
            success {
                 archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
                 junit 'build/reports/**/*.xml'
           }
        }
}
