<div class="axi-header">
  <h1>Ingest using Logstash</h1>
</div>

**NOTE:** Currently You can only ship logs to Axiom using the Logstash versions [7.12](https://www.elastic.co/guide/en/beats/libbeat/7.12/index.html) and lower. 

---

## Logstash

Logstash is an open source log aggregation, transformation tool and server-side data processing pipeline that ingests data from a multitude of sources simultaneously. With Logstash, you can collect, parse, ingest and store logs for future use on **Axiom**.

Logstash works as a Data pipeline tool with Axiom, where from one end the data is input from your servers and system and from the other end **Axiom** takes out the data and converts it into useful information.

It can read data from various `input` sources , filter data for the specified configuration and eventually stores the data.
Logstash sits between your data and where you want to store it.

### Installation 

Visit the [Logstash download page](https://www.elastic.co/downloads/logstash) to install Logstash on your system.

### Configuration

To configure the `logstash.conf` file, you have to define the source, set the rules to format your data and also set **Axiom** as the destination where the data will be forwarded to. 

The Logstash Pipeline has three stages:

- **Input stage:** which generates the event & Ingest Data of all volumes, Sizes, forms and Sources
- **Filter stage:** modifies the event as you specify in the filter component 
- **Output stage:** shifts and sends the event into **Axiom.** 

---

In `logstash.conf`, configure your `logstash pipeline` to collect and send data logs to **Axiom**

The example below shows Logstash configuration that sends data to Axiom:

=== "Conf"

```conf
input{
  exec{
    command => "date"
    interval => "1"
  }
}
output{
  elasticsearch{
    hosts => ["$YOUR_AXIOM_URL:443/api/v1/datasets/<dataset>/elastic"]
    # api_key can be your ingest or personal token
    api_key => "user:token"
    ssl => true
  }
}
```




