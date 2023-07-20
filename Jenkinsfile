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
                        echo 'Unit Test'
                    }
                }
                 stage('Code Review') {
                    steps {
                        echo 'Code Review'
                    }
            }
         }
        }
    }
}