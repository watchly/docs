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

