<div class="axi-header">
  <h1>Get Started with the Axiom API</h1>
</div>

The best way to get started with our API is to use [Go-Axiom](https://github.com/axiomhq/axiom-go) to send events directly to Axiom API.

Axiom understands your resources and provides an API to ingest structured data logs, handle and manage your deployments. This is a **REST-style** API that uses JSON for serialization and OAuth 2 for authentication. 

This page covers the basics for interacting with the Axiom API, plus instructions for ingesting data and notes on some commonly used endpoints.


Also, we have two API clients for your convenience:

- Go Client 

- JS Client

## Make a Request 

All URLs start with https://<axiomurl>/api/v1/tokens/ingest. The path is prefixed with the API version.

## Ingesting structured Data


**POST /api/v1/tokens/ingest/**

### Responses

**Example as a curl command**

```
  curl -X POST \
    "https://<axiom-url>/api/v1/tokens/ingest" 
    -H  "accept: application/json" 
    -H  "Content-Type: application/json" 
    -d "{  \"description\": \"string\",  \"name\": \"string\",  \"scopes\": [    \"string\"  ]}"
```
#### More examples

```

curl -X 'POST' 'https://<axiom-url>/api/v1/datasets/<dataset>/ingest' \
  -H 'Authorization: Bearer $INGEST_TOKEN' \
  -H 'Content-Type: application/x-ndjson' \
  -d '{ "path": "/download", "method": "GET", "duration_ms": 231, "res_size_bytes": 3012 }'

```

### Request URL

https://<axiom_url>/api/v1/tokens/ingest

### Response 

| **Code** | **Description**                          |
|----------------|-----------------------------------------------------|
|     200  | {
  "description": "string",
  "id": "string",
  "name": "string",
  "scopes": [
    "string"
  ]
} |














