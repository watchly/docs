<div class="axi-header">
  <h1>Ingest using Axiom Loki Proxy</h1>
</div>

Axiom Loki Proxy is a push interface to Axiom via Loki endpoint. 

> Loki exposes an HTTP API for pushing, querying, and tailing log data.

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
