# Research Data Visualizer
## Introduction

## Getting Started
1) Edit stack.yaml to add appropriate paths for InfluxDB data, Grafana data, and Ingest data.
2) Create the appropriate data structure with telegraf config files in the ingest data directory. An example of this structure is included in ./example-ingest-directory
```
example-ingest-directory/
├── DATA.dat
└── config
    ├── DATA.conf
```
3) Start a docker swarm cluster and launch the stack
```
docker swarm init
docker stack deploy rdv --compose-file stack.yaml
```
4) The Grafana web interface can now be accessed by navigating to http://localhost:3000

5) When changing the telegraf config files in the ingest directory, you must send a SIGHUP to the telegraf process to apply the changes.
```
docker kill <TELEGRAF_CONTAINER_ID> -s SIGHUP
```
