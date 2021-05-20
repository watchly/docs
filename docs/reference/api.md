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

## Make a Request 

All URLs start with https://<axiomurl>/api/v1/tokens/ingest. The path is prefixed with the API version.

## Ingesting structured Data

1. **POST /api/v1/tokens/ingest/**

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

**Request URL**

```

https://<axiom_url>/api/v1/tokens/ingest

```

**Response**

| **Content type ** | **application/json** |
|----------------|-------------|

Code = 200

```
{
  "description": "string",
  "id": "string",
  "name": "string",
  "scopes": [
    "string"
  ]
}
```

2. **GET /api/v1/tokens​/ingest**

**Example as a curl command**

```

curl -X GET "https://<axiom_url>/api/v1/tokens/ingest" -H  "accept: application/json"

```

**Request URL**

```

https://<axiom_url>/api/v1/tokens/ingest

```

**Response**

| **Content type ** | **application/json** |
|----------------|-------------|

Code = 200

```
[
  {
    "description": "string",
    "id": "string",
    "name": "string",
    "scopes": [
      "string"
    ]
  }
]
```

3. **DELETE /api/v1​/tokens​/ingest​/{id}**

**Example as a curl command**

```

curl -X DELETE "https://<axiom_url>/api/v1/tokens/ingest/string" -H  "accept: application/json"

```

**Request URL**

```
https://<axiom_url>/api/v1/tokens/ingest/string

```
**Response**

| **Content type ** | **application/json** |
|----------------|-------------|

Code = 

```

```

4.  **GET /api/v1/tokens​/ingest​/{id}**

**Example as a curl command**

```

curl -X GET "https://<axiom_url>/api/v1/tokens/ingest/string" -H  "accept: application/json"

```

**Request URL**

```
https://<axiom_url>/api/v1/tokens/ingest/string

```

| **Content type ** | **application/json** |
|----------------|-------------|

Code = 200

```
{
  "description": "string",
  "id": "string",
  "name": "string",
  "scopes": [
    "string"
  ]
}
```

5. **PUT /api/v1/tokens​/ingest​/{id}**

**Example as a curl command**

```

curl -X PUT "https://<axiom_url>/api/v1/tokens/ingest/string" -H  "accept: application/json" -H  "Content-Type: application/json" -d "{  \"description\": \"string\",  \"id\": \"string\",  \"name\": \"string\",  \"scopes\": [    \"string\"  ]}"

```

**Request URL**

```
https://<axiom_url>/api/v1/tokens/ingest/string

```

| **Content type ** | **application/json** |
|----------------|-------------|

Code = 200

```
{
  "description": "string",
  "id": "string",
  "name": "string",
  "scopes": [
    "string"
  ]
}
```

6. **GET /tokens​/ingest​/{id}​/token**

**Example as a curl command**

```

curl -X GET "https://axicode.axiom.co/api/v1/tokens/ingest/string/token" -H  "accept: application/json"

```

**Request URL**

```

https://axicode.axiom.co/api/v1/tokens/ingest/string/token

```

| **Content type ** | **application/json** |
|----------------|-------------|

Code = 200

```
{
  "scopes": [
    "string"
  ],
  "token": "string"
}

```




















#### GET/tokens​/ingest​/{id}

| **Content type ** | **application/json** |
|----------------|-------------|

Code = 200

```{
  "description": "string",
  "id": "string",
  "name": "string",
  "scopes": [
    "string"
  ]
}
```

#### PUT/tokens​/ingest​/{id}

| **Content type ** | **application/json** |
|----------------|-------------|


Code = 200

```{
  "description": "string",
  "id": "string",
  "name": "string",
  "scopes": [
    "string"
  ]
}
```

#### GET/tokens​/ingest​/{id}​/token

| **Content type ** | **application/json** |
|----------------|-------------|

Code = 200

```
{
  "scopes": [
    "string"
  ],
  "token": "string"
}
```




















