<div class="axi-header">
  <h1>Ingest using Logstash</h1>
</div>

## Logstash

Logstash is an open source log aggregation and transformation tool and server-side data processing pipeline that ingests data from a multitude of sources simultaneously. With Logstash, you can transforms your data, and send it directly to **Axiom**. 

It can read data from various `input` sources , **filter data** for the specified configuration and eventually **stores the data.**
Logstash sits between your data and where you want to store it. 

### Installation 

Visit the [Logstash download page](https://www.elastic.co/downloads/logstash) to install Logstash on your system.

### Configuration

To configure the `logstash.conf` file, you have to define the source, set the rules to format the data and also set **Axiom** as the destination where the data will be forwarded to. 

The Logstash Pipeline has three stages:
- Input stage: which generates the event & Ingest Data of all volumes, Sizes, forms and Sources
- Filter stage: modifies the event as you specify in the filter component 
- Ouput stage: shifts the event it to Axiom. 




