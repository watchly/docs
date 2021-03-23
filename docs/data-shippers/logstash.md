<div class="axi-header">
  <h1>Ingest using Logstash</h1>
</div>

## Logstash

Logstash is an open source log aggregation and transformation tool and server-side data processing pipeline that ingests data from a multitude of sources simultaneously. With Logstash, you can transforms your data, and send it directly to **Axiom**. 

It can read data from various `input` sources , **filter data** for the specified configuration and eventually **stores the data.**
Logstash sits between your data and where you want to store it. 

The Logstash Pipeline has three stages:
- Input stage: which generates the event & Ingest Data of all volumes, Sizes, forms and Sources
- Filter stage: modifies the event as you specify in the filter component 
- Ouput stage: shifts the event it to Axiom. 

The input and output stages are required elements whereas the filter element is an optional 

### Installation 

Visit the [Logstash download page](https://www.elastic.co/downloads/logstash) to install Logstash on your system.


