<p align="center"><img src="documentation/collect250.png" alt="logo data collector" width="250" height="250"/> </p>
<p align="center"><h1 align="center"> Smart City Platform - Data Collector</h1></p>

![Build Status](https://gitlab.com/smart-city-software-platform/data-collector/badges/master/build.svg)
[![Mezuro](https://img.shields.io/badge/mezuro-green-green.svg)](http://mezuro.org/en/repositories/73)
[![Mezuro](https://img.shields.io/badge/freenode-%40data__collector-blue.svg)]()

---

# Welcome to Data Collector

> The *Data Collector*'s main goal is to provide methods to search data collected
from *Resources*.

> This service is used both by applications and the Catalog Service, and offers
developers access to information coming from different sensors scattered
throughout the city. For example, with this service one could obtain data of
all temperature sensors on USP.

# Architecture

<p align="center"><img src="documentation/pci-overview-datacollector.png" alt="Architecture Diagram" /></p>

# How to use

> We developed a [step-by-step](https://gitlab.com/smart-city-software-platform/data-collector/wikis/basic-setup) to configure the application.
After configure the application, it should be possible to request data and filter it by some parameters.

> We developed a [manual](https://gitlab.com/smart-city-software-platform/data-collector/wikis/home) to understand our API.In this manual can be found a data structure used to return the data and some usage examples.

> We developed a [pub/sub](https://gitlab.com/smart-city-software-platform/data-collector/wikis/pub-sub) system,to be possible receive a notification every time that a new data is collected.

# Setup and references

> If you need help, look at:

> * [Basic setup](https://gitlab.com/smart-city-software-platform/data-collector/wikis/basic-setup)
> * [Publish/Subscribe](https://gitlab.com/smart-city-software-platform/data-collector/wikis/pub-sub)
> * [Our API](https://gitlab.com/smart-city-software-platform/data-collector/wikis/home)
> * [Base architecture overview](http://s32.postimg.org/a16hueg79/Arquitetura_geral_da_plataforma_de_cidades_intel.jpg)
> * Data Collector's [Class Diagram](documentation/ClassDiagram.png)

# Docker setup

* Install Docker and docker-compose (versão 1.6+): (google it)
* Run on terminal:
  * `$ scripts/setup`
  * `$ scripts/development start` # start the container
  * `$ scripts/development stop`  # stop the container
  * `$ scripts/development exec data-collector <command>` # run a command into data-collector container
  * **(OPTIONAL):** `$ scripts/development exec data-collector rake db:seed`

Now you can access the application on http://localhost:4000

## Workaround

Please, try the following approaches to fix possible errors raised when 
trying to start docker services:

### Bind problem

If you have bind errors while trying to start a docker service, try
to remove the docker-network **platform** and create it again. If this not fix
the problem, run the following commands:

* Stop docker deamon: ```sudo service docker stop```
* Remova o arquivo local-kv: ```sudo rm /var/lib/docker/network/files/local-kv.db```
* Start docker deamon: ```sudo service docker start```
* Create the network again: ```sudo docker network create platform```
* Run the container: ```./script/development start```

### Name problem

If get any name conflicts while trying to run a docker container, try to 
follow these steps:

* Stop current container: ```./script/development stop```
* Start the container: ```./script/development start```
