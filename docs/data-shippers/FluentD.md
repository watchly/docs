<div class="axi-header">
  <h1>Ingest using FluentD</h1>
</div>


FluentD is an open-source software for collecting, aggregating, processing, analyzing and routing log files. 

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
- Matches: Send output to **Axiom** when input data matches and pair specific data from your data input within your configuration. 
- Labels:  Groups filters and simplifies tag handling. 

When setting up your fluentD, the configuration file is used to connect its components. 

In the configuration file, inputs are defined 

=== "Conf"

```conf
## built-in TCP input
## $ echo <json> | fluent-cat <tag>
<source>
  @type forward
  @id forward_input
</source>

## built-in UNIX socket input
#<source>
#  @type unix
#</source>

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

<match *.**>
  @type           elasticsearch
  hosts "$YOUR_AXIOM_URL:443/api/v1/datasets/<dataset>/elastic"
  api_key "user:token"
  verify_es_version_at_startup false
</match>
```

