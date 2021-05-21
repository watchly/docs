<div class="axi-header">
  <h1>Get Started with the Axiom API</h1>
</div>

The best way to get started with our API is to use [Go-Axiom](https://github.com/axiomhq/axiom-go) to send events directly to Axiom API.

Axiom understands your resources and provides an API to ingest structured data logs, handle and manage your deployments. This is a **REST-style** API that uses JSON for serialization and OAuth 2 for authentication. 

This page covers the basics for interacting with the Axiom API, plus instructions for ingesting data and notes on some commonly used endpoints.

## Authentication

Axiom uses OAuth2 for authentication. All requests must use HTTPS.

You can generate a ingest token in your Axiom user settings for manual authentication in shell scripts or commands that use the Axiom API. Refer to the code sample below for an example of how to use this token in a curl request.


Also, we have two API clients for your convenience:

- Go Client 

- JS Client

## Ingesting data

Individual events are ingested as an HTTP POST request.



### Using curl command to ingest data

`POST /api/v1/ingest/` 

```

curl $YOUR_AXIOM_URL/api/v1/ingest/ \
 -X POST \
 -H "Content-Type: application/json" \
 -H "Authorization: Bearer $INGEST_TOKEN" \
 -d '[{"tags": {"host":"myserver"}, "events" : [{"timestamp": "2016-06-06T12:00:00+02:00", "attributes": {"key1":"value1"}}]}]'

```

```

curl -X POST "https://axicode.axiom.co/api/v1/ingest" 
  -H  "accept: application/json" -H  "Content-Type: application/json" 
  -d "{  \"description\": \"string\",  \"name\": \"string\",  \"scopes\": [    \"string\"  ]}"

```

### Body Specification 

The body of the POST should be a JSON encoded object containing key/value pairs. As an example, to report a GET request from the users `/download path` took 231ms:

```
curl -X 'POST' 'https://azure1.staging.axiomtestlabs.co/api/v1/datasets/neil-cmc/ingest' \
  -H 'Authorization: Bearer xait-96ac7408-c7d1-4cde-9e23-d1bda820636a' \
  -H 'Content-Type: application/x-ndjson' -H 'x-axiom-org-id: axiom' \
  -d '{ "path": "/download", "method": "GET", "duration_ms": 231, "res_size_bytes": 3012 }'

```

Supported data types:

- strings
- numbers
- booleans

curl -X 'POST' 'https://azure1.staging.axiomtestlabs.co/api/v1/datasets/neil-cmc/ingest' \
  -H 'Authorization: Bearer xait-96ac7408-c7d1-4cde-9e23-d1bda820636a' \
  -H 'Content-Type: application/x-ndjson' -H 'x-axiom-org-id: axiom' \
  -d ''

---

Datasets name are usually case sensitive, **Dataset names must be between 1-128 characters, and may only contain ASCII alphanumeric characters and the '-' character.**

When sending an Event, you can set the following standard fields:

**Name** |        **Description**                  |
|-----------------|-----------------------------------------------------------|
| duration_ms         |    You can specify the time duration |
| method  |   | HTTP Methods
|  path |   path of your file   |
|  res_size_bytes |      |
|id   |  |
|name|   |
|scopes ||

---

Axiom supports ingestion of different data formats:

- application/json
- application/nd-json
- text/csv

## Ingest Tokens

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






