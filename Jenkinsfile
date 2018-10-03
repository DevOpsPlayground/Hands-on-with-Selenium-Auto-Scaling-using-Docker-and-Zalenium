#!groovy

node('master') {

    def dockerTool = tool name: 'docker', type: 'org.jenkinsci.plugins.docker.commons.tools.DockerTool'
    withEnv(["DOCKER=${dockerTool}/bin"]){

    stage('Checkout') {
        checkout scm
        echo 'Repository checked out'
    }

    stage('Run Zalenium') {
        dockerCmd 'run --rm -ti --name zalenium -d -p 4444:4444 \
            -v /var/run/docker.sock:/var/run/docker.sock \
            -v /tmp/videos:/home/seluser/videos \
            --privileged dosel/zalenium start'
        echo 'Zalenium running'
    }
}
}
