# Scorpio NGSI-LD Broker
Scorpio ist ein NGSI-LD-konformer Kontextbroker , der von NEC Laboratories Europe und NEC Technologies India entwickelt wurde. Er implementiert die vollständige NGSI-LD-API gemäß der Spezifikation der ETSI Industry Specification Group on cross cutting Context Information Management (ETSI ISG CIM).

## TL;DR

```bash
$ helm install scorpio ./helm -n scorpio --create-namespace
```

## Introduction
This chart bootstraps a ScorpioBroker deployment on a Kubernetes cluster using the Helm package manager.

## Prerequisites

* Kubernetes 1.30+
* Helm 3.8.0+

## Installing the chart

Check out this repository and install the chart

```bash
$ cd scorpiobroker
$ helm install <my-release> helm --values <values file> -n <namespace>
```

or you can use:

```bash
$ helm upgrade --install <my-release> helm --values <values file> -n <namespace>
```

To install the chart with release name my-release in namespace my-namespace:

```bash
$ helm upgrade --install my-release helm -n my-namespace --create-namespace --values <values file>
```

## Parameters
| Name                    | Description                                     | Value                      |
|:------------------------|:------------------------------------------------|:---------------------------|
| env.postgreSQL          | PostgreSQL service name                         | postgresql.scorpio.svc     |
| service.type            | ServiceType                                     | ClusterIP                  |
| service.port            | Scorpio Service port                            | 9090                       |
| ingress.enabled         | Enable ingress                                  | false                      |
| ingress.className       | ClassName of ingress                            | ""                         |
| resources.requests.cpu  |                                                 | 200m                       |
| resources.request.memory|                                                 | 512Mi                      |
| rabbitmq.enabled        | Enable and use RabbitMQ                         | false                      |
| rabbitmq.config.hostname|                                                 | rabbitmq                   |
| rabbitmq.config.username|                                                 | ""                         |
| rabbitmq.config.password|                                                 | ""                         |
| config.ngsildCoreContext|                                                 | https://uri.etsi.org/ngsi-ld/v1/ngsi-ld-core-context-v1.8.jsonld |
| config.quarkusLogLevel  |                                                 | INFO                       |
| config.quarkusVertxEventLoopsPoolSize |                                   | 20                         |
| config.scorpioDirectDb  |                                                 | true                       |
| config.scorpioHistoryAutorecording |                                      | false                      |
| config.scorpioHistoryMaxLimit |                                           | 100                        |
| config.scorpioHistoryDefaultLimit |                                       | 50                         |
| config.scorpioFedupdaterate |                                             | 600s                       |
| config.scorpioSubscriptionCheckInterval |                                 | 4s                         |

## Troubleshooting

There is currently no troubleshooting guide available.

## Upgrading the chart

To upgrade the chart with the release name my-release:

```bash
$ helm upgrade <my-release> helm --values <values file> -n <namespace>
```

## License

Copyright © 2024 ADDIX GmbH.

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.