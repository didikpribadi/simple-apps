pipeline {
    agent {
        node {
            label 'devops-didik'
        }
    }

    stages {
        stage('Build Apps') {
            steps {
               sh 'npm install'
            }
        }

        stage('Run Test') {
            parallel{
                stage('Unit Test') {
                    steps {
                        sh '''npm test
                        npm run test:coverage'''
                    }
                }
                 stage('Code Review') {
                    steps {
                      sh 'sonar-scanner   -Dsonar.projectKey=project-didik   -Dsonar.sources=.   -Dsonar.host.url=http://10.23.2.2:9000   -Dsonar.login=sqp_970980f3a97d40438778cd6c6ed880154f4e9fb9'
                    }
                }
            }
        }

        stage('Build Image') {
            steps {
              sh 'docker compose build'
            }
        }

        stage('Push Image') {
            steps {
              sh 'docker compose push'
            }
        }

        stage('Deploy Apps') {
            steps {
              sh 'docker compose up -d'
            }
        }
    }
}