<div class="axi-header">
  <h1>Ingest using FluentD</h1>
</div>


FluentD is an open-source software for collecting, aggregating, processing, analyzing and routing log files. 

With FluentD you can collect logs from multiple sources and ship it instantly into **Axiom**

---

### Installation

---

### Configuration

FluentD lifecycle consist of five different components which are:

- Setup: Configure your `fluent.conf` file. 
- Inputs: Define your listeners. 
- Filters: Create a rule to allow or disallow an event. 
- Matches:Send output to **Axiom** when input data matches and pair specific data from your data input within your configuration. 
- Labels: 

When setting up your fluentD, the configuration file is used to connect its components. 

In the configuration file, inputs are defined 