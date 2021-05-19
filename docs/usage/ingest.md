<div class="axi-header">
  <h1>Ingesting Data</h1>
</div>

Ingest, transport and fetch data from different sources such as Relational database, web logs, batch data, real-time, application logs, streaming data, etc for later usage using the Axiom API. 

You can also Collect, load, group, move, data from one or more sources to Axiom where it can be stored and further analyzed.

Before ingesting data, you will need an API Token which you can generate from the **Settings->Tokens** page on the Axiom Dashboard. See [API Tokens documentation](/usage/settings#api-tokens).

<br />
 Once you have an ingest token, there are three ways to get your data into Axiom:

1. Using the [Ingest API](#ingest-api)
2. Using a [Data Shipper](#data-shippers) (Logstash, Filebeat, Metricbeat, Fluentd etc)
4. Using the [Elasticsearch Bulk API](/data-shippers/api) that Axiom supports natively

## Ingest API

Axiom exports a simple REST API that can accept any of the following formats:

- `application/json` - single event or json array of events
- `application/nd-json`- structured data processed at a time
- `text/csv` - this should include the header line with field names

=== "cURL"

    ```bash
      curl -X POST \
        -H "Authorization: Bearer <INGEST_TOKEN>" \
        -H "Content-Type: application/x-ndjson" \
        -d '{ "this": "is", "an": "example", "json": 1 }' \
        https://<axiom-url>/api/v1/datasets/<my-dataset>/ingest
    ``` 

If you would like to instead use a language binding, currently our Golang client library is available:

- [axiom-go](https://github.com/axiomhq/axiom-go)

More client libraries are coming very soon!

---

### Limits

| Kind                      | Limit |
| ------------------------- | ----: |
| Maximum Event Batch Size  |  1000 |
| Maximum Event Fields      |   250 |
| Maximum Array Field Items |   100 |

## Data Shippers

Configure, read, collect, and Send logs to your Axiom deployment using a variety of data shippers. Data shippers are lightweight agents that acquire logs, metrics, and lets you ship data directly into Axiom. 

---

<a class="axi-link-button" href="/data-shippers/api/" title="API Compatibility">
  <img src="/assets/integrate.svg" width=24 alt="integrations icon" />
  <span>Ingest using API</span>
  <img src="/assets/chevron-right.svg" width=16 alt="go" />
</a>

---

<a class="axi-link-button" href="/data-shippers/elastic-beats/" title="Elastic Beats">
  <img src="/assets/integrate.svg" width=24 alt="integrations icon" />
  <span>Ingest using Elastic Beats</span>
  <img src="/assets/chevron-right.svg" width=16 alt="go" />
</a>

---

<a class="axi-link-button" href="/data-shippers/fluentd" title="FluentD">
  <img src="/assets/integrate.svg" width=24 alt="integrations icon" />
  <span>Ingest using FluentD</span>
  <img src="/assets/chevron-right.svg" width=16 alt="go" />
</a>

---

<a class="axi-link-button" href="/data-shippers/kubernetes-filebeat" title="Kubernetes">
  <img src="/assets/integrate.svg" width=24 alt="integrations icon" />
  <span>Ingest using Kubernetes</span>
  <img src="/assets/chevron-right.svg" width=16 alt="go" />
</a>

---

<a class="axi-link-button" href="/data-shippers/logstash" title="Logstash">
  <img src="/assets/integrate.svg" width=24 alt="integrations icon" />
  <span>Ingest using Logstash</span>
  <img src="/assets/chevron-right.svg" width=16 alt="go" />
</a>

---

<a class="axi-link-button" href="/data-shippers/loki" title="Loki">
  <img src="/assets/integrate.svg" width=24 alt="integrations icon" />
  <span>Ingest using Loki Proxy</span>
  <img src="/assets/chevron-right.svg" width=16 alt="go" />
</a>

---

<a class="axi-link-button" href="/data-shippers/syslog-proxy" title="Syslog">
  <img src="/assets/integrate.svg" width=24 alt="integrations icon" />
  <span>Ingest using Syslog Proxy</span>
  <img src="/assets/chevron-right.svg" width=16 alt="go" />
</a>



