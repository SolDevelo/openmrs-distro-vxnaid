# Vxnaid OpenMRS

This project contains Vxnaid OpenMRS distribution application.
It has been tailored for quick-evaluation of Vxnaid features and as a base for production builds.

The Docker and Docker Compose are required to run this project. 
The included scripts and Docker configuration are made for Unix environments.

The complete Vxnaid system consists of:
* this OpenMRS application
* Neurotechnology server which facilitates biometrics
* Android mobile app

More information about other components of Vxnaid system can be found in the Vxnaid user manual.

## Running the Vxnaid OpenMRS

The Vxnaid OpenMRS package is located in the `cfl` directory of this project. 
The `cfl` directory contains detailed  `README.md` which describes how to start this application in quick evaluation called
dev-mode, and how to build and run Docker image of the Vxnaid OpenMRS distribution for more production-like
 environments.

### Quick start

To start the Vxnaid OpenMRS distribution application on your local Unix machine:

1. Create `cfl/.env` file, 
    1. use `cfl/.env.example`
    1. set `INITIAL_STARTUP=true`
1. Run: `cfl/runInDevMode.sh`

It will create and start Docker containers for MySQL db and Tomcat with the application. 

**Be wary**, the initial startup performs time-consuming, one-time operations which can take up to tens of minutes.
