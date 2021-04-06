<div class="axi-header">
  <h1>Ingest using Syslog</h1>
</div>

Logs are generated on all Network devices, Axiom Syslog Proxy ships logs to Axiom, acting as a Syslog server.

With Syslog logging system, you can monitor events on your devices and send them directly into **Axiom**, this also helps you retain your data logs. 

The udp log messages is sent on `UDP` port `514` to the syslog server. 

The tcp log messages is sent on `TCP` port `601` to the syslog server. 
## Installation

You can Download the Binary releases available on [GitHub Releases.](https://github.com/axiomhq/axiom-syslog-proxy/releases/tag/v0.1.4)

### Install using Homebrew

```shell
$ brew tap axiomhq/tap
$ brew install axiom-syslog-proxy
```

### Install using go get

```shell
$ go get -u github.com/axiomhq/axiom-syslog-proxy/cmd/axiom-syslog-proxy
```

### Install from source

```bash
$ git clone https://github.com/axiomhq/axiom-syslog-proxy.git
$ cd axiom-syslog-proxy
$ make build
```

### Pull and Run the Docker image 

```shell 
$ docker pull axiomhq/axiom-syslog-proxy:latest
```

## Configuration

---

- Specify the environmental variables for your Axiom deployment

AXIOM_DEPLOYMENT_URL: URL of the Axiom Deployment to use. 

AXIOM_ACCESS_TOKEN: Personal Access or Ingest token. Your personal access or ingest token can be created under Profile or Settings > Ingest Tokens.

AXIOM_INGEST_DATASET:  Dataset to ingest into

- Run it:

```shell
$ ./axiom-syslog-proxy
```

Using Docker

```shell
$ docker run -p601:601/tcp -p514:514/udp  \
  -e=AXIOM_DEPLOYMENT_URL=<AXIOM_DEPLOYMENT_URL> \
  -e=AXIOM_ACCESS_TOKEN=<AXIOM_ACCESS_TOKEN> \
  -e=AXIOM_INGEST_DATASET=<AXIOM_INGEST_DATASET> \
  axiomhq/axiom-syslog-proxy
```

- Test it:

```shell
$ echo -n "tcp message" | nc -w1 localhost 601
$ echo -n "udp message" | nc -u -w1 localhost 514
```

---

For more information on Axiom-loki-proxy and how you can propose bug fix, fill issues and submit PRs, kindly visit out repository on [Github](https://github.com/axiomhq/axiom-syslog-proxy). 









