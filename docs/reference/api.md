<div class="axi-header">
  <h1>Get Started with the Axiom API</h1>
</div>

The best way to get started with our API is to use [Go-Axiom](https://github.com/axiomhq/axiom-go) to send events directly to Axiom API.

Axiom understands your resources and provides an API to ingest structured data logs, handle and manage your deployments. This is a **REST-style** API that uses JSON for serialization and OAuth 2 for authentication. 

This page covers the basics for interacting with the Axiom API, plus instructions for ingesting data and notes on some commonly used endpoints.

## Authentication

Axiom uses OAuth2 for authentication. All requests must use HTTPS.

You can generate a ingest token in your Axiom user settings for manual authentication in shell scripts or commands that use the Axiom API. Refer to the code sample below for an example of how to use this token in a curl request.

### API Tokens

Axiom has two types of API tokens; 

- Personal API Tokens.
- Ingest Tokens.

### Personal API Token; 

The personal token can be retrieved from the users profile page, all users have a Personal Token. With the Personal Token users can access the Axiom API programmatically for custom integrations, management setting, or for tools such as the Axiom CLI.

The personal access token grants access to all resources available to the user on his behalf.  

Personal Access or Ingest token. Can be created under **Profile** or **Settings > Profile > Personal Tokens.**

<img class="axi-window-shadow" src="/assets/shots/personal-token.png" alt="Personal Token overview" /> 


### Ingest Token

Ingest Tokens just allows ingestion into the datasets the token is configured for. Use ingest tokens to send data to one or more datasets. Ingest tokens do not allow control of your organization, they are only used to ingest events. 

**For security reasons it is advised to use an Ingest Token with minimal privileges only.**

You can obtain the Ingest Token from the settings > Ingest Token of the Axiom deployment.

<img class="axi-window-shadow" src="/assets/shots/ingest-token.png" alt="Ingest Token overview" /> 


Also, we have two API clients for your convenience:

- Go Client 

- JS Client

## Ingesting data

`POST /api/v1/ingest/` 

Individual events are ingested as an HTTP POST request.


### Using curl command to ingest data


```
curl -X POST '$YOUR_AXIOM_URL/api/v1/ingest' \
  -H 'Authorization: Bearer $INGEST_TOKEN' \
  -H 'Content-Type: application/x-ndjson' \
  -d "{  \"description\": \"string\",  \"name\": \"string\",  \"scopes\": [    \"string\"  ]}"

```

## Body Specification 

The body of the POST should be a JSON encoded object containing key/value pairs. As an example, to report a GET request from the users `/download path took 231ms with a response size of 3012`. 

```
{ "path": "/download", "method": "GET", "duration_ms": 231, "res_size_bytes": 3012 }'

```

## Examples 

These examples sends an API event to Axiom. It is in the `neil-cmc` dataset.


## Ingest Events using NDJSON

`NDJSON` consists of individual lines where each individual line is any valid JSON text and each line is delimited with a newline character. The `NDJSON` payload should have the scheme of `{"id":1,"name":"Alice"} {"id":2,"name":"Bob"} {"id":3,"name":"Carol"}`


### Example Request using NDJSON 

```
curl -X 'POST' '$YOUR_AXIOM_URL/api/v1/datasets/neilcmc/ingest' \
  -H 'Authorization: Bearer $INGEST_TOKEN' \
  -H 'Content-Type: application/x-ndjson' -H 'x-axiom-org-id: axiom' \
  -d '{ "path": "/download", "method": "POST", "duration_ms": 231, "res_size_bytes": 3012, "endpoint":"/foo" }'

```

#### More examples

```

curl -X 'POST' '$YOUR_AXIOM_URL/api/v1/datasets/neil-cmc/ingest' \
  -H 'Authorization: Bearer $INGEST_TOKEN' \
  -H 'Content-Type: application/x-ndjson' -H 'x-axiom-org-id: axiom' \
  -d '{"container": {"image": "front:master.0326.5","name": "tunnel-front"},"labels": {"component": "tunnel","pod-template-hash": "75f5666499"},"namespace": "kube-system","node": {"name": "32068356-vmss000002"},"pod": {"name": "fnxln","uid": "f0bdea4e57"},"replicaset": {"name": "75f5666499"}}}'

```

### Example Response

```

A successful POST Request returns a standard HTTP 200 response code.

```

---

## Ingest Events using JSON

The following example request contains grouped events. The structure of the `JSON` payload should have the scheme of `[ { "labels": { "key1": "value1", "key2": "value12" } }, ]` in which the array comprises of one or more JSON objects describing Events.

### Example Request using JSON

```

curl -X 'POST' '$YOUR_AXIOM_URL/api/v1/datasets/neilcmc/ingest' \
  -H 'Authorization: Bearer $INGEST_TOKEN' \
  -H 'Content-Type: application/json' -H 'x-axiom-org-id: axiom' \
  -d '[
        {
          "time":"2021-23-04302:11:23.222Z",
          "data":{"key1":"value1","key2":"value2"}
        },
        {
          "data":{"key3":"value3"},
          "labels":{"key4":"value4"}
        }
      ]'

```

### Grouping Events with different Labels

You can also group events with different labels into the same request as shown below: 

```
curl -X 'POST' '$YOUR_AXIOM_URL/api/v1/datasets/neilcmc/ingest' \
  -H 'Authorization: Bearer $INGEST_TOKEN' \
  -H 'Content-Type: application/json' -H 'x-axiom-org-id: axiom' \
  -d '[
  {
    "labels": {
      "author": "System1",
      "model": "whip.log"      $YOUR_HUMIO_URL/api/v1/ingest
    },
    "events": [
      {
        "timestamp": "2020-05-04T11:00:00+06:00",
        "elements": {
          "foo": "bar"
        }
      },
      {
        "timestamp": "2020-05-04T12:00:01+03:00",
        "attributes": {
          "status": "202",
          "address": "/src.php"
        }
      }
    ]
  },
  {
    "labels": {
      "author": "System2",
      "model": "whip.log"
    },
    "events": [
      {
        "timestamp": "2020-05-04T13:00:02+02:00",
        "attributes": {
          "key2": "value2"
        }
      }
    ]
  },
  {
    "labels": {
      "author": "System3",
      "model": "whip.log"
    },
    "events": [
      {
        "timestamp": "2020-05-04T14:00:03+02:00",
        "attributes": {
          "key3": "value3",
          "status": "200"
        }
      }
    ]
  }
]'

```

### Example Response

```

A successful POST Request returns a standard HTTP 200 response code.

```

## Ingest Events using CSV


The following example request contains events. The structure of the `CSV` payload uses a comma to separate values ['value1', 'value2', 'value3'].

### Example Request using CSV

```
curl -X 'POST' '$YOUR_AXIOM_URL/api/v1/datasets/neil-cmc/ingest' \
  -H 'Authorization: Bearer $INGEST_TOKEN' \
  -H 'Content-Type: text/csv' -H 'x-axiom-org-id: axiom' \
  -d '['name', 'area', 'country_code2', 'country_code3']'

```

### Example Response

```

A successful POST Request returns a standard HTTP 200 response code.

```

---

Supported data types:

- strings
- numbers
- Arrays of objects
- booleans

---

Datasets name are usually case sensitive, Dataset names must be between 1-128 characters, and may only contain ASCII alphanumeric characters and the '-' character.

---

Axiom supports ingestion of different data formats:

- application/json
- application/nd-json
- text/csv