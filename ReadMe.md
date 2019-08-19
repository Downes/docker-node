This sets up a Node Express Server inside a Docker container. It is set up for Windows.

1. To run, start a terminal in this directory and run the command:

    docker-compose run --rm --service-ports nod_dev_env

    If the ports in docker-compose.yml are in use, change them using this command instead:

    docker-compose run --rm -p 4000:3000 nod_dev_env

2. To start the node server, then from inside the container, run the command:

    yarn start


To restart server at any time, type: rs


Open a new instance of the running container shell:

    docker exec -it $(docker ps -qf "name=node-docker") /bin/bash

Make a server request using the internal port 3000:

    docker exec -it $(docker ps -qf "name=node-docker") curl localhost:3000

Install or remove dependencies:

    docker exec -it $(docker ps -qf "name=node-docker") yarn add body-parser






Note: if you get an error
   Cannot create container for service nod_dev_env: b'Drive has not been shared'
then you need to enable sharing on your directory. See:
https://github.com/docker/compose/issues/4854