#!groovy

node('master') {
    stage('Checkout') {
        checkout scm
        echo 'Repository checked out'
    }

    stage('Start Zalenium')
    {
        sh 'docker run --rm -ti --name zalenium -d -p 4444:4444 \
            -v /var/run/docker.sock:/var/run/docker.sock \
            -v /tmp/videos:/home/seluser/videos \
            --privileged dosel/zalenium start'
    }
    
    stage('Run tests') {
         {
            sh './node_modules/.bin/wdio wdio.conf.js'
          }
      }
    }
}
