Base from : [OpenTelemetry Dotnet](https://github.com/open-telemetry/opentelemetry-dotnet)

TODO:
* Adicionar docker compose para subir serviços do rabbitmq e zipkin

# OpenTelemetry Example Application

This set of projects is an example distributed application comprised of two
components:

1. An ASP.NET Core Web API
2. A background Worker Service

The application demonstrates a number of OpenTelemetry concepts:

* OpenTelemetry APIs for distributed context propagation.
* Basic conventions of how messaging systems are handled in OpenTelemetry.

The Web API publishes messages to RabbitMQ which the Worker Service consumes.
Distributed context propagation is achieved using OpenTelemetry APIs to inject
and extract trace context in the headers of the published messages.

The Zipkin exporter is configured for viewing the distributed traces.

## Running the example

A running instance of RabbitMQ and Zipkin are required. These can easily be
spun up in docker containers.

The `WebApi` and `WorkerService` projects can be run from this directory as
follows:

```shell
dotnet run --project WorkeApi
dotnet run --project WorkerService
```


With everything running:

* [Invoke the Web API](http://localhost:5000/SendMessage) to send a message.
* If you have run RabbitMQ and Zipkin with default settings:
  * Manage RabbitMQ by accessing the local endpoint
  [http://localhost:15672/](http://localhost:15672/)
    * user = guest
    * password = guest
  * View your traces with Zipkin by accessing the local endpoint
  [http://localhost:9411/zipkin](http://localhost:9411/zipkin).


## References

* [Docker Desktop](https://www.docker.com/products/docker-desktop)
* [OpenTelemetry Project](https://opentelemetry.io/)
* [RabbitMQ](https://www.rabbitmq.com/)
* [Worker Service](https://docs.microsoft.com/azure/azure-monitor/app/worker-service)
* [Zipkin](https://zipkin.io)
* [OpenTelemetry Dotnet](https://github.com/open-telemetry/opentelemetry-dotnet)
