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