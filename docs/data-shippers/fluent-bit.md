<div class="axi-header">
  <h1>Ingesting using Fluent-Bit</h1>
</div>

## Fluent Bit

Fluent Bit is an open source Log Processor and Forwarder which allows you to collect any data like metrics and logs from different sources, enrich them with filters and send them to multiple destinations like **Axiom**. 

### Installation 

Visit the [Fluent Bit download page](https://docs.fluentbit.io/manual/installation/getting-started-with-fluent-bit) to install Fluent Bit on your system. 

### Configuration

Fluent Bit configuration file supports four types of sections:

- Service: Defines global properties of your service using different keys available for a specific version.
- Input: Defines the input plugin and base configuration of your file. 
- Filter: Defines the input plugin and configure the pattern tags for your configuration. 
- Output: Specify a destination that certain records should follow after a Tag match. 

All sections will be configured in your `.conf` file. 

#### example

The example below shows fluent Bit configuration that sends data to Axiom:

=== "Conf"

```conf

  [SERVICE]
      Flush           5
      Daemon          off
      Log_Level       debug


  [INPUT]
      Name  cpu
      Tag   cpu


  [OUTPUT]
      Name  http
      Match *
      Host  cloud.axiom.co
      Port  443
      URI   /api/v1/datasets/<my-dataset>/ingest
      Header Authorization Bearer xait-xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx
      compress On
      format json
      json_date_key _time
      json_date_format iso8601
      tls On

```