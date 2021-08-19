# Docker Compose for Databases

This repository is intended for storing docker compose configs for running Database servers locally. Each of the ```.yml``` file contains 1 or 2 services to run as containers.

Following are the instructions to run the databases locally.

Prerequisites:
- Docker Engine is installed and is able to run containers, confirm with

```docker run hello-world```

Output (maybe a little-bit different):

```
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

- You should also have Docker Compose installed and running, confirm with

```docker-compose --version```

Output (version maybe different)

```
docker-compose version 1.29.2, build 5becea4c
```

### Running a PostgreSQL database and pgAdmin

Run the following command:

```docker-compose -f postgres.yml up```

The ```docker``` will pull the required images from the DockerHub and run the containers (only one time).

If successful, you should be able to access your pgAdmin at ```localhost:8082``` and login with following credentials:

Email: postgres@example.com
Password: postgres

And access the database server through the pgAdmin, user and password: ```postgres```


### Running a Mongo database and Mongo Express

Run the following command:

```docker-compose -f mongo.yml up```

If successful, you should be able to access the Mongo Express at ```localhost:8083```


### Running a Oracle database

The oracle image needs to be built and then we can create a container and utilize the ```docker-compose```.

So, for only the first time, follow the instructions [here](https://github.com/oracle/docker-images/tree/main/OracleDatabase/SingleInstance) for building a single instance container image. Be sure to use build the ```11.2.0.2-xe``` version as it is in referenced in the ```oracle.yml``` file. You may change the version according to your need and build the corresponding container. Also blog [here](https://medium.com/idomongodb/oracle-18-4-xe-on-a-docker-container-5fe8e434a34e) can be helpful.

After you are done, run:

```docker-compose -f oracle.yml up```

If successful you should be able to access the database using ```sqlplus``` commandline util.