<div class="axi-header">
  <h1>Ingesting Via Loki</h1>
</div>

Loki by Prometheus, is a multi-tenant log aggregation system that is highly scalable and capable of indexing metadata about your logs.

Loki exposes an HTTP API for pushing, querying, and tailing Axiom log data.

**Axiom Loki Proxy** enables a push interface to Axiom via Loki endpoint. 

With **Axiom-Loki-Proxy**, you can ships logs to Axiom via the  [Loki HTTP API](https://grafana.com/docs/loki/latest/api/#post-lokiapiv1push). 

## Installation

### Install & Update using Homebrew

```shell
$ brew tap axiomhq/tap
$ brew install axiom-loki-proxy
$ brew update
$ brew upgrade axiom-loki-proxy
```

### Install using `go get`

```shell
$ go get -u github.com/axiomhq/axiom-loki-proxy/cmd/axiom-loki-proxy
```

### Install from source

```shell
$ git clone https://github.com/axiomhq/axiom-loki-proxy.git
$ cd axiom-loki-proxy
$ make build
```

### Run the Loki-Proxy Docker [image](https://hub.docker.com/r/axiomhq/axiom-loki-proxy)

```shell
$  docker pull axiomhq/axiom-loki-proxy:latest
```

## Configuration

---

- Specify the environmental variables for your Axiom deployment

**AXIOM_DEPLOYMENT_URL:** URL of the Axiom Deployment to use. 

AXIOM_URL is always in this format -> **https://cloud.axiom.co**

**AXIOM_ACCESS_TOKEN:** Personal Access or Ingest token. Your personal access or ingest token can be created under Profile or Settings > Ingest Tokens.

**For security reasons it is advised to use an Ingest Token with minimal privileges only.**

- Run & Test it:

```shell
./axiom-loki-proxy
```

Using Docker

```
$ docker run -p3101:3101/tcp \
  -e=AXIOM_DEPLOYMENT_URL=<AXIOM_DEPLOYMENT_URL> \
  -e=AXIOM_ACCESS_TOKEN=<AXIOM_ACCESS_TOKEN> \
  axiomhq/axiom-loki-proxy
```

---

For more information on Axiom-loki-proxy and how you can propose bug fix, fill issues and submit PRs, kindly visit out repository on [Github](https://github.com/axiomhq/axiom-loki-proxy). 




