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
    }
}