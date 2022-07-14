<p align="center">
  <a href="https://massa.net/" target="blank"><img src="https://massa.net/_nuxt/img/logo_massa.989057b.webp" width="300" alt="Massa Logo" /></a>
</p>

<p align="center">A project for creating and monitoring a <a href="https://massa.net/" target="_blank">Massa</a> node.</p>

## Description

The goal of this project is to provide the configuration to create and manage a stack of different tools in order to create and monitor a Massa node.

This stack is composed of:
- A Massa node: [rykcod/massa](https://github.com/rykcod/massa)
- An agent that collects the information of the node and exposes them on a websocket: [massa-node-agent](https://github.com/fsidhoum/massa-node-agent)
- An adapter that connects to the websocket to get the data and populate an InfluxDb database: [massa-node-infludb-adapter](https://github.com/fsidhoum/massa-node-influxdb-adapter)
- An InfluxDb database with its webapp: [influxdb](https://github.com/influxdata/influxdb)

## Prerequisites

[Docker](https://docs.docker.com/engine/install/) and [docker-compose](https://docs.docker.com/compose/) needs to be installed.

## Installation

### Cloning this repository

```bash
$ git clone https://github.com/fsidhoum/massa-node-stack.git
$ cd massa-node-stack
```

### Create the file `.env`
```dotenv
# Massa
MASSA_VERSION=episode13.0.0
MASSA_DATA_FOLDER=/tmp

# Massa Node Agent
MASSA_NODE_AGENT_VERSION=1.0.0

# Massa Node InfluxDB Adapter
MASSA_NODE_INFLUX_ADAPTER_VERSION=1.0.0

# InfluxDb
INFLUXDB_VERSION=2.3.0-alpine
INFLUXDB_DATA_FOLDER=/tmp
```

Change the values according to your setup.

### Create the file `.massa-env` (optional)
Fill this file with the environment variables you need to define for the Docker container of the Massa node.

See the [doc](https://github.com/rykcod/massa#run-usecase-example) for more details about the environment variables that can be defined.

### Create the file `.massa-node-agent-env` (optional)
Fill this file with the environment variables you need to define for the Docker container of the Massa node agent.

See the [doc](https://github.com/fsidhoum/massa-node-agent#environment-variables) for more details about the environment variables that can be defined.

### Create the file `.massa-node-influxdb-adapter-env` (optional)
Fill this file with the environment variables you need to define for the Docker container of the Massa node InfluxDb adapter.

See the [doc](https://github.com/fsidhoum/massa-node-influxdb-adapter#environment-variables) for more details about the environment variables that can be defined.

### Create the file `.influxdb-env` (optional)
Fill this file with the environment variables you need to define for the Docker container of InfluxDb.

See the [doc](https://github.com/docker-library/docs/tree/master/influxdb#using-this-image---influxdb-2x) for more details about the environment variables that can be defined.

### Run the stack

```shell
$ docker-compose up -d
```
