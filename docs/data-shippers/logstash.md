<div class="axi-header">
  <h1>Ingest using Logstash</h1>
</div>

## Logstash

Logstash is an open source log aggregation and transformation tool and server-side data processing pipeline that ingests data from a multitude of sources simultaneously. With Logstash, you can transforms your data, and send it directly to **Axiom**. 

It can read data from various `input` sources , **filter data** for the specified configuration and eventually **stores the data.**
Logstash sits between your data and where you want to store it. 

In simplistic terms its a naive forwarder in which you define source , you set the rules to format the data and you define the destination where to forward the data.

INPUTS: Ingest Data of All Shapes, Sizes, and Sources
FILTERS: Parse & Transform Your Data On the Fly
OUTPUTS: Choose Your Stash, Transport Your Data

The Logstash Pipeline has three stages:
- Input stage: which generates the event & Ingest Data of all volumes, Sizes, forms and Sources
- Filter stage: modifies the event as you specify in the filter component 
- Ouput stage: shifts the event it to Axiom. 

The input and output stages are required elements whereas the filter element is an optional 

### Installation 

Visit the [Logstash download page](https://www.elastic.co/downloads/logstash) to install Logstash on your system.

### Configuration




