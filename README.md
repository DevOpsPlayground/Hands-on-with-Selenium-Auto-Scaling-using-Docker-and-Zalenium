# Auto-Scaling Selenium Grid with Docker and Zalenium

## Accessing Your Machine

We will provide you with a machine IP address which is your Ubuntu VM for the duration of tonight's DevOps Playground.

1. To access your machine first open a Terminal/Command window and enter the following command:
    `ssh @devops{yourIp}`
    
    The password for all machines is `playground`. 

## What Have We Already Set Up?

- Docker - https://docs.docker.com/
- Selenium WebDriver Test Suite - https://github.com/ecsdigital/devopsplayground-edi-8-zalenium 

## Installing Zalenium and Docker-Selenium

To install Zalenium and Selenium for Docker. 

1. To install docker-selenium run the following command in your ssh session:
    `docker pull elgalu/selenium`

2. To install Zalenium, run the following command in your ssh session:
    `docker pull dosel/zalenium`

## Running Zalenium

1. In your ssh terminal/command window enter the following:

     ```
     docker run --rm -ti --name zalenium -p 4444:4444 \
     -v /var/run/docker.sock:/var/run/docker.sock \
     -v /tmp/videos:/home/seluser/videos \
     --privileged dosel/zalenium start
     ```

The above command runs Zalenium and exposes port 4444. 
It allows Zalenium to create more Selenium Grid docker containers.
It sets a local location for videos to be saved. 
Running it privileged is optional, but it does help to speed up the registration of containers.

2. In a few seconds, access http://{yourIp}:4444/grid/console in your browser on your local machine.
    You should see two docker-selenium containers with one instance each of Firefox and Chrome. This is by default.

## Running Zalenium - Running a Selenium Test



