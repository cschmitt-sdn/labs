# labs
## Prerequisites:
- git installlation:
https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

- docker installation:
https://docs.docker.com/get-docker/

- docker-compose installation:
https://docs.docker.com/compose/install/

## Start the lab:
1. Clone the github repository on your server:
`git clone https://github.com/cschmitt-sdn/labs.git`
This repository contains 2 folders (sfx and locust), this README and a docker-compose-yml file

For your information:
- In the `locust` folder, the `locustfile.py` is the script which is being used by the Locust Load Generator
- In the `sfx` folder are all needed files for the SignalFx agent to run.

The docker-compose.yaml contains all information needed for the labs to start-up:
It starts:
- an elasticsearch docker instance for the FoodTruck application named __es__
- a web application (foodtruck) named __foodtruck__ instrumented with the uAPM agent from SignalFx
- a SignalFx agent named __sfx_agent__
- a locust Load Generator named __locust__ in order to generate some load on our application

2. Modify the docker-compose file so that you get a unique service name. Find the line with *SIGNALFX_SERVICE_NAME=FoodTruck_YOURNAME* and replace *YOURNAME*

3. Start the lab:
`docker-compose -up -d`

If you go to SignalFx, you can then be able to see load generated on your service.



## Change the application version
1. Modify the docker-compose. Find the `image: daz-labs.jfrog.io/foodtruck-web:1.0.0` line and change the version with __1.0.1__
So it should look like : `image: daz-labs.jfrog.io/foodtruck-web:1.0.1`

You should then see a difference in the response time and load in SignalFx
