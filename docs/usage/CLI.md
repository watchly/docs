<div class="axi-header">
  <h1>Axiom CLI</h1>
</div>

## Get started with Axiom CLI

Axiom's command line interface (CLI) is an Axiom tool that lets you test, manage, and build your Axiom deployments/instances/projects by typing commands on the command-line. 

You can use the command line to Ingest data, manage authentication state, and configure multiple deployments. 

## Installation

To install Axiom CLI, make sure you have [Go](https://golang.org/dl/) version 1.15 or higher, then run this command from any directory in your terminal. 

=== "Go"

    ```bash
    $ go get -u github.com/axiomhq/cli/cmd/axiom
    ```

---

You can also install the CLI using [Homebrew](https://brew.sh/) 

=== "Brew"

    ```bash
    $ brew tap axiomhq/tap
    $ brew install axiom 
    ```
This installs Axiom command globally so you can run `axiom` commands from any directory. 

---

Install from source using the native [go mod](https://golang.org/cmd/go/#hdr-Module_maintenance) support

=== "Bash"

    ```Bash
    $ git clone https://github.com/axiomhq/cli.git
    $ cd cli
    $ make install # Build and install binary into $GOPATH
    ```

---

Install & Run the Docker image

=== "Bash"

    ```Bash
    $ docker pull axiomhq/cli
    $ docker run axiomhq/cli  
    ```


You can check the version and find out basic commands about the tool with the following command:

=== "bash"

```
$ axiom
```

## Authentication 

You can manage the authentication state of your deployments with the Axiom command-line interface. It's possible for you to log in, log out of, select an Axiom deployment, and view the authentication status of your deployments. 

Before logging in, you are being asked for your account credentials interactively on the command line, enter your various credentials, and log into your specified deployment. The resulting token is printed out for further use or stored in the configuration file alongside the instance URL and alias to refer to it in the future. 

<img class="axi-crop" src="/assets/shots/cli-authentication.gif" alt="Cli-authentication"/>


**Axiom CLI uses a personal or ingest token to authenticate with Axiom. You can obtain this token via the [Axiom UI](/usage/settings/#token).** 

## Session support

You can configure multiple Axiom deployments using the Axiom CLI by configuring the appropriate endpoint and auth token. The configuration is obtained from the configuration file or the environment: `~/.config/.axiom.toml`

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
AX_URL="https://axiom.mycompany.com"
AX_TOKEN="XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"

# Select an Axiom instance from the available ones configured in
# "~/.config/axiom/backends.yml" by using its alias, overriding the
# preference in the config file:
AX_BACKEND="main-instance"

```

## Obtain a token in the Axiom UI

**To generate an ingest Token**

1. under **settings**, select **ingest token**. 
2. Select **Add ingest token**.
3. Enter a **name** and **description** and select **ADD**. 
4. Copy the generated token to your clipboard. Once you navigate from the page, token can be seen again by selecting **Ingest Tokens**. 

**To generate a Personal Token**

1. Under **settings**, select **profile**
2. Select **Add personal token**
3. Enter a **name** and **description** and select **ADD**.
4. Copy the generated token to your clipboard. Once you navigate from the page, token can be seen again by selecting **Personal token**

## Configuration and Deployment 

Axiom CLI lets you ingest, authenticate, and stream data. 

For more information about Configuration, managing authentication status, ingesting, streaming, and more, 
visit the [Axiom CLI](https://github.com/axiomhq/cli) repository on GitHub. 

## Ingestion

Import, transfer, load and process data for later use or storage using the Axiom CLI move data from o Axiom CLI supports the ingestion of different formats of data ( JSON, NDJSON, and CSV) 

**To view a list of all the available commands run `axiom` on your terminal:** 

=== "Shell"

```bash
➜ ~ axiom

The power of Axiom on the command-line.

USAGE
  axiom <command> <subcommand> [flags]

CORE COMMANDS
  ingest:     Ingest data
  stream:     Livestream data

MANAGEMENT COMMANDS
  auth:       Manage authentication state
  config:     Manage configuration
  dataset:    Manage datasets

ADDITIONAL COMMANDS
  completion: Generate shell completion scripts
  help:       Help about any command
  version:    Print version

FLAGS
  -C, --config string       Path to configuration file to use
  -D, --deployment string   Deployment to use
  -h, --help                Show help for command
  -T, --token string        Token to use
  -U, --url string          Url to use
  -v, --version             Show axiom version

EXAMPLES
  $ axiom auth login
  $ cat /var/log/nginx/*.log | axiom ingest -d nginx-logs
  $ axiom query -d nginx-logs

ENVIRONMENT VARIABLES
  See 'axiom help environment' for the list of supported environment variables.

LEARN MORE
  Use 'axiom <command> <subcommand> --help' for more information about a command.
  Read the manual at https://docs.axiom.co/cli

```

## Get help

To get usage tips and learn more about available commands from within Axiom CLI, run the following:

=== "bash"
```
$ axiom help
```

For more information about a specific command, run `help` with the name of the command. 

=== "bash"
```
$ axiom help auth 
```

This also works for sub-commands.

=== "bash"
```
$ axiom help auth status
```

**if you have questions, or any opinions you can [start an issue](https://github.com/axiomhq/cli/issues) on Axiom CLI's open source repository.**


**You can also visit our [Slack group]() to start or join a discussion. We’d love to hear from you!**





