#!groovy

pipeline('master'){

    stages {

        stage('Checkout') {
            steps{
            checkout scm
            echo 'Repository checked out'
            }
        }

                stage('Run Zalenium') {
                    steps{
            sh 'docker run --rm -ti --name zalenium -d -p 4444:4444 \
                -v /var/run/docker.sock:/var/run/docker.sock \
                -v /tmp/videos:/home/seluser/videos \
                --privileged dosel/zalenium start'
            echo 'Zalenium running'
                    }
        }    
    }
}
