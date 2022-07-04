# Description
Run Vxnaid Distribution.

The distribution project consists of docker compose configuration files and resources which make up a Vxnaid distribution
 (OpenMRS Web Application, modules and other).

The project contains **.env.example** file which contains the configuration of an environment, the committed version
 configures Vxnaid distribution to run on your local docker, where both application and database docker containers are
  running. 

The docker compose configuration files, with suffix .yml, should stay unchanged - with an exception of docker image
 versioning.
 
**Increment proper version number in docker-compose.run.yml and docker-compose.build.yml when you make any
 change in this project**

## Requirements
  - Docker engine
  - Docker compose

## Development

The project provides utility script to start OpenMRS application docker container together with MySQL container.

Run script:
```runInDevMode.sh```

## Production

Build Vxnaid distribution image using ``docker-compose.build.yml``.

```
sudo docker-compose -f docker-compose.build.yml build web
```

Save Vxnaid distribution image into archive. 

```
sudo docker save openmrsvxnaid:X.Y.Z | gzip > openmrsvxnaid.Y.Z.tar.gz
```

Distribute the created image together with ``docker-compose.run.yml`` file. 
The ``.env`` file has to be created during installation, each environment has individual configuration.

### Run production

Configure ``.env`` accordingly to the production environment.

Load Vxnaid distribution image.

```
sudo docker load < openmrsvxnaid.Y.Z.tar.gz
```

Run docker-compose.run.yml configuration

```
sudo docker-compose -f docker-compose.run.yml up -d web
```

Inspect logs

```
sudo docker logs -f --tail 500 cfl_web_1
```
