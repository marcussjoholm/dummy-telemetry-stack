# Dummy grafana stack
Spins up a local grafana with:

* [Grafana](https://grafana.com/grafana/)
* [Alloy](https://grafana.com/docs/alloy/latest/)
* [Loki](https://grafana.com/products/cloud/logs/)
* [Prometheus](https://prometheus.io/)

and a dummy service that emits random logs and metrics to be scraped by the observability stack.

> [!NOTE]
> This dummy stack is humbly forked from the Grafana Labs workshop https://github.com/grafana/dashboards-as-code-workshop for working with observability as code. I highly recommend going through this workshop/lab yourself to familiarize yourself with the Grafana Foundation SDK and the Grafana CLI (`grafanactl`)

Start the stack using Docker:

```shell
docker compose -f docker-compose.yaml up --build
```

> [!TIP]
> Verify that the Grafana instance is accessible at [`http://localhost:3000`](http://localhost:3000)

## Install the Grafana CLI

[Grafana CLI](https://grafana.github.io/grafanactl/) (*grafanactl*) is a
command-line tool designed to simplify interaction with Grafana instances.

Follow the [installation instructions](https://github.com/grafana/grafanactl/blob/main/docs/installation.md#prebuilt-binaries) in its documentation.

> [!TIP]
> Verify that `grafanactl` is installed and runs:
>
> ```shell
> grafanactl --version
> ```

## Configure `grafanactl`

With `grafanactl` installed, configure it to connect to the lab's Grafana instance:

```shell
grafanactl config set contexts.default.grafana.server http://localhost:3000
grafanactl config set contexts.default.grafana.org-id 1
```

> [!TIP]
> Check that `grafanactl` can indeed connect to the stack:
>
> ```shell
> grafanactl config check
> ```
