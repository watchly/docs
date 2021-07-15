<div class="axi-header">
  <h1>Ingest using FluentD</h1>
</div>

## FluentD

FluentD is an open-source log collector that allows you to collect, aggregate, process, analyze and route log files. 

With FluentD you can collect logs from multiple sources and ship it instantly into **Axiom**

---

### Installation

Visit the [FluentD download page](https://www.fluentd.org/download) to install FluentD on your system. 

---
### Configuration

FluentD lifecycle consist of five different components which are:

- Setup: Configure your `fluent.conf` file. 
- Inputs: Define your input listeners. 
- Filters: Create a rule to allow or disallow an event. 
- Matches: Send output to **Axiom** when input data match and pair specific data from your data input within your configuration. 
- Labels:  Groups filters and simplifies tag handling. 

When setting up fluentD, the configuration file `.conf` is used to connect its components. 

---

The example below shows fluentD configuration that sends data to Axiom:

=== "Conf"

```conf
# FluentD is listening for forward, monitor agent and debug agent using the source element. 
# built-in TCP input
# $ echo <json> | fluent-cat <tag>

<source>
  @type forward
  @id forward_input
</source>

<source>
  @type monitor_agent
  @id monitor_agent_input
  port 24220
</source>

# Listen DRb for debug
<source>
  @type debug_agent
  @id debug_agent_input
  bind 127.0.0.1
  port 24230
</source>

## matches the input and sends output to **Axiom host**
<match *.**>
  @type           elasticsearch

  ## host is the url of your Axiom deployment
  hosts "https://cloud.axiom.co/api/v1/datasets/<my-datasets>/elastic"

  ## api_key can be your ingest or personal token
  api_key "user:token"

  verify_es_version_at_startup false
</match>
```