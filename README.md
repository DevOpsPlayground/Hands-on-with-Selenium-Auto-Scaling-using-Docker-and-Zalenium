# Auto-Scaling Selenium Grid with Docker and Zalenium

##Accessing Your Machine

##What Have We Already Set Up?

- Docker - https://docs.docker.com/docker-for-windows/install/#install-docker-for-windows-desktop-app
- Zalenium - https://github.com/zalando/zalenium/blob/master/README.md#getting-started
- Selenium WebDriver Test Suite - 

##Running Zalenium - Basic Example

1. In a command/terminal window:

     ```
     docker run --rm -ti --name zalenium -p 4444:4444 \
     -v /var/run/docker.sock:/var/run/docker.sock \
     -v /tmp/videos:/home/seluser/videos \
     --privileged dosel/zalenium start
     ```

     HINT: In future you can use a CURL command to start Zalenium
     `curl -sSL https://raw.githubusercontent.com/dosel/t/i/p | bash -s start`


The above command runs Zalenium and exposes port 4444. 
It allows Zalenium to create more Selenium Grid docker containers.
It sets a local location for videos to be saved. 
Running it privileged is optional, but it does help to speed up the registration of containers.

2. In a few seconds, access http://localhost:4444/grid/console in your browser.
    You should see two docker-selenium containers with one instance each of Firefox and Chrome. This is by default.

3. To stop the process press CTRL + C.

##Running Zalenium - Running a Selenium Test



