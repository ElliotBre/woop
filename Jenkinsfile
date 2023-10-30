pipeline {
    agent any
    stages{
        stage('Test') {
            steps {
                sh 'ls -a'
                sh 'pwd'
            }
        }
        stage('Build') {
            steps {
                sh 'touch example.txt'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo hello >> example.txt'
                sh 'cat example.txt'
            }
        }
    }
}
