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
     --privileged dosel/zalenium start &
     ```

    The above command runs Zalenium and exposes port 4444.  
    It allows Zalenium to create more Selenium Grid docker containers.  
    It sets a local location for videos to be saved.  
    Running it privileged is optional, but it does help to speed up the registration of containers.  
    & allows us to continue using the same terminal/command window.  

2. In a few seconds, access http://{yourIp}:4444/grid/console in your browser on your local machine.
    You should see two Selenium Grid containers with one instance each of Firefox and Chrome. This is by default.

## Running Zalenium - Running a Selenium Test

1. In your ssh terminal/command window, navigate to the JavaScript WebDriver.io repository
` `

2. To run the tests, enter the following command
`./node_modules/.bin/wdio wdio.conf.js`

Whilst this is running, observe the number of Selenium Grid containers being created (http://{yourIp}:4444/grid/console) as the tests are being run.

Once the tests are finishing you can perform a refresh on the Console page to see the number of instances scale down.

You can also view recorded videos by accessing http://{yourIp}:4444/dashboard. This provides you with a history of the tests which have been run and a video recording of these tests.

## Closing Zalenium

1. Once your tests are finished you will probably want to shut down Zalenium. To do this enter the following command:

`docker stop zalenium`

To verify that this has closed correctly, access the Console page (http://{yourIp}:4444/grid/console). You should have a page not found error.

