# Elastic APM connector

The Elastic APM connector aggregates Elastic APM-specific metrics from signals.

<!-- status autogenerated section -->
| Status        |           |
| ------------- |-----------|
| Distributions | [] |
| Warnings      | [Statefulness](#warnings) |
| Issues        | [![Open issues](https://img.shields.io/github/issues-search/elastic/opentelemetry-collector-components?query=is%3Aissue%20is%3Aopen%20label%3Aconnector%2Felasticapm%20&label=open&color=orange&logo=opentelemetry)](https://github.com/elastic/opentelemetry-collector-components/issues?q=is%3Aopen+is%3Aissue+label%3Aconnector%2Felasticapm) [![Closed issues](https://img.shields.io/github/issues-search/elastic/opentelemetry-collector-components?query=is%3Aissue%20is%3Aclosed%20label%3Aconnector%2Felasticapm%20&label=closed&color=blue&logo=opentelemetry)](https://github.com/elastic/opentelemetry-collector-components/issues?q=is%3Aclosed+is%3Aissue+label%3Aconnector%2Felasticapm) |

[development]: https://github.com/open-telemetry/opentelemetry-collector/blob/main/docs/component-stability.md#development

## Supported Pipeline Types

| [Exporter Pipeline Type] | [Receiver Pipeline Type] | [Stability Level] |
| ------------------------ | ------------------------ | ----------------- |
| logs | metrics | [development] |
| metrics | metrics | [development] |
| traces | metrics | [development] |

[Exporter Pipeline Type]: https://github.com/open-telemetry/opentelemetry-collector/blob/main/connector/README.md#exporter-pipeline-type
[Receiver Pipeline Type]: https://github.com/open-telemetry/opentelemetry-collector/blob/main/connector/README.md#receiver-pipeline-type
[Stability Level]: https://github.com/open-telemetry/opentelemetry-collector/blob/main/docs/component-stability.md#stability-levels
<!-- end autogenerated section -->

## Configuration

By design, this component has minimal configuration. An empty configuration will be functional
though we would not recommend this for production workloads; aggregation state should be stored
on disk to avoid extreme memory usage under high throughput.

By default, all aggregation state is maintained in-memory. The aggregation state can be stored
on disk instead by specifying `elasticapm::aggregation::directory`, which should be a directory
dedicated to this purpose.

By default, aggregated metrics will be exported without any client metadata. It is possible to
propagate client metadata from input to exported metrics by specifying a list of metadata keys
in `elasticapm::aggregation::metadata_keys`.

```yaml
elasticapm:
  aggregation:
    directory: /path/to/aggregation/directory
    metadata_keys: [list, of, metadata, keys]
```
