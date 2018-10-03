#!groovy

node('master') {

    agent {
        docker { image 'node:7-alpine' }
    }
        stage('Checkout') {
            checkout scm
            echo 'Repository checked out'
        }
}
