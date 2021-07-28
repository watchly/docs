<div class="axi-header">
  <h1>Axiom CLI</h1>
</div>

## Get started with Axiom CLI

Axiom's command line interface (CLI) is an Axiom tool that lets you test, manage, and build your Axiom deployments and projects by typing commands on the command-line. 

You can use the command line to Ingest data, manage authentication state, and configure multiple deployments. 

## Installation

### Install using go get

To install Axiom CLI, make sure you have [Go](https://golang.org/dl/) version 1.15 or higher, then run this command from any directory in your terminal. 

=== "Go"

```bash
go get -u github.com/axiomhq/cli/cmd/axiom
```

### Install using Homebrew

You can also install the CLI using [Homebrew](https://brew.sh/) 

=== "Brew"

```bash
brew tap axiomhq/tap
brew install axiom 
```
This installs Axiom command globally so you can run `axiom` commands from any directory.

To update:

=== "Brew"

```bash
brew upgrade axiom
```

### Install from source

```sh
git clone https://github.com/axiomhq/cli.git
cd cli
make install # Build and install binary into $GOPATH

```
### Run the Docker image

Docker images are available on [DockerHub.](https://hub.docker.com/r/axiomhq/cli)

```sh
docker pull axiomhq/cli
docker run axiomhq/cli

```

You can check the version and find out basic commands about Axiom CLI by running the following command:

=== "bash"
```sh
axiom

```
## Authentication 

You can manage the authentication state of your deployments with the Axiom command-line interface. It's possible for you to log in, log out of, select an Axiom deployment, and view the authentication status of your deployments. 

Before logging in, you are being asked for your account credentials interactively on the command line, enter your various credentials, and log into your specified deployment. The resulting [token](/usage/settings/#token) is printed out for further use or stored in the configuration file alongside the instance URL and alias to refer to it in the future. 

<img class="axi-crop" src="/assets/shots/cli-authentication.gif" alt="Cli-authentication"/>


**Axiom CLI uses a personal or ingest token to authenticate with Axiom. You can obtain this token via the [Axiom UI](/usage/settings/#token).**

## Session support

You can configure multiple Axiom deployments using the Axiom CLI by configuring the appropriate endpoint and [auth token.](/usage/settings/#token) The configuration is obtained from the configuration file or the environment: `~/.config/.axiom.toml`

<img class="axi-crop" src="/assets/shots/cli-session-support.gif" alt="Cli-session"/>

=== "Yaml"

```
active-backend: main-instance
backends:
- main-instance:
  url: https://axiom.mycompany.com
  user: username@axiom.co
  token: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
- alt-instance:
  url: https://axiom-2.mycompany.com
  user: username@axiom.co
  token: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

```
To view available environment variables run `axiom help environment` for an up to date list of env vars: 

=== "Shell"

```
# Directly set an Axiom instance:
AX_URL="https://cloud.axiom.co"
AX_TOKEN="XaptXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"

# Select an Axiom instance from the available ones configured in
# "~/.config/axiom/backends.yml" by using its alias, overriding the
# preference in the config file:
AX_BACKEND="main-instance"

```

## Tokens

You can generate an ingest and personal token manually in your Axiom user settings.

See [Tokens](/usage/settings/#token) to know more about managing access and authorization. 

## Configuration and Deployment 

Axiom CLI lets you ingest, authenticate, and stream data. 

For more information about Configuration, managing authentication status, ingesting, streaming, and more, 
visit the [Axiom CLI](https://github.com/axiomhq/cli) repository on GitHub. 

Axiom CLI supports the ingestion of different formats of data **( JSON, NDJSON, and CSV)** 

## Ingestion

Import, transfer, load and process data for later use or storage using the Axiom CLI. With [Axiom CLI](https://github.com/axiomhq/cli) you can Ingest the contents of a **JSON, NDJSON, CSV** logfile into a dataset.  


**To view a list of all the available commands run `axiom` on your terminal:** 

=== "Shell"

```bash
➜ ~ axiom
The power of Axiom on the command-line.

USAGE
  axiom <command> <subcommand> [flags]

CORE COMMANDS
  ingest:      Ingest data
  stream:      Livestream data

MANAGEMENT COMMANDS
  auth:        Manage authentication state
  config:      Manage configuration
  dataset:     Manage datasets
  organization:Manage organizations

ADDITIONAL COMMANDS
  completion:  Generate shell completion scripts
  help:        Help about any command
  version:     Print version

FLAGS
  -C, --config string       Path to configuration file to use
  -D, --deployment string   Deployment to use
  -h, --help                Show help for command
  -I, --insecure            Bypass certificate validation
  -O, --org-id string       Organization ID to use (only valid for Axiom Cloud)
  -T, --token string        Token to use
  -U, --url string          Url to use
  -v, --version             Show axiom version

EXAMPLES
  $ axiom auth login
  $ axiom version
  $ cat /var/log/nginx/*.log | axiom ingest nginx-logs

AUTHENTICATION
  See 'axiom help credentials' for help and guidance on authentication.

ENVIRONMENT VARIABLES
  See 'axiom help environment' for the list of supported environment variables.

LEARN MORE
  Use 'axiom <command> <subcommand> --help' for more information about a command.
  
  Read the manual at https://docs.axiom.co/reference/CLI/

```
## Command reference 

View and Get started with [Axiom CLI Command List here.](https://github.com/axiomhq/cli#commands)

## Get help

To get usage tips and learn more about available commands from within Axiom CLI, run the following:

=== "bash"
```
axiom help
```

For more information about a specific command, run `help` with the name of the command. 

=== "bash"
```
axiom help auth 

```

This also works for sub-commands.

=== "bash"
```
axiom help auth status

```

**if you have questions, or any opinions you can [start an issue](https://github.com/axiomhq/cli/issues) on Axiom CLI's open source repository.**

---

**You can also visit our [Slack group](https://www.axiom.co/support/) to start or join a discussion. We’d love to hear from you!**