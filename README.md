# Deploying the OpenTelemetry Collector with your application
The OpenTelemetry (OTel) collector runs alongside your application to scrape logs and send telemetry data to LightFoot's observability backend storage. The OTel collector is configured as a docker container that can be spun up on the same machine as your application.

In the case where you are deploying your application, the OTel collector, and the backend storage all on the same machine, follow the instructions for **Local Deployment** below. 

In the case where you are deploying your application and the OTel collector on the same machine, but the backend storage on another machine, follow the instructions for **Distributed Deployment** below.

## Using the .env file
For both distributed and local deployment, you will need a `LOG_PATH` variable in your .env file. This will hold the path to your logs in your application folder:

```
LOG_PATH=path/to/your/application/logs
```

For **Distributed Deployment**, you will add two more variables - the IP addresses and ports for Tempo and Loki from the machine you have deployed the observability backend storage to:

```
TEMPO_ENDPOINT=<IP Address>:4317
LOKI_ENDPOINT=<IP Address>:3100/loki/api/v1/push
```

## Local Deployment
First, run `docker compose up` for the observability backend. Then, run `docker compose up` in this otel-collector directory to spin up the collector.

## Distributed Deployment
Add the needed variables for Loki and Tempo endpoints to your .env file in this directory. Then, run `docker compose up`
