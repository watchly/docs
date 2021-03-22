<<<<<<< HEAD
<<<<<<< HEAD
<div class="axi-header">
  <h1>Frequently Asked Questions</h1>
</div>

This page includes frequently asked questions from users which we feel help to build a better understanding of Axiom and how best to use it. If you cannot find an answer to your own questions, please do not hesitate to [contact us](support@axiom.co).

## What is Axiom?

Axiom is log management and analytics solution that reduces the cost and management overhead of logging as much data as you want.

With Axiom, organizations no longer need to choose between their data and their costs. Axiom has been built from the ground-up to allow for highly efficient data ingestion and storage, and then a zero-to-infinite query scaling that allows you to query all your data, all the time.

Organizations use Axiom for continuous monitoring & observability, as well as an event store for running analytics and deriving insights from all their event data.

Axiom consists of a datastore and a user-experience that work in tandem to provide a completely unique log-management & analytics experience.

## Where does Axiom run?

Axiom is a self-host software product that runs right inside of your infrastructure. Your infrastructure can be cloud VPCs or metal, Axiom can be run anywhere.

Axiom only requires a Postgresql database and an object store to run. There is no requirement for Apache Kakfa, Zookeeper, or any other dependency that would be a headache to maintain.

AWS S3, Azure, Google Cloud, DigitalOcean, Minio, and Ceph are all supported object stores and so Axiom is at home almost anywhere.


## Is there an Axiom Cloud?

Not at this moment, but it is coming soon (Q1 2021). If you would like to register your interest, then please sign up below to be notified:


<script charset="utf-8" type="text/javascript" src="//js.hsforms.net/forms/shell.js"></script>
<script>
  hbspt.forms.create({
	portalId: "7714395",
	formId: "b959af05-de2b-4177-9d26-f785874416b8"
});
</script>


## How is Axiom different than other logging solutions?

At Axiom, our goal is that no organization has to ignore or delete a single piece of data no matter its source: logs, events, frontend, backends, audits, etc.

We found that existing solutions would place restrictions on how much data can be collected either on purpose or as a side-effect of their architectures.

For example: the “state of the art” in logging is running stateful clusters that need shared knowledge of ingestion and will use a mixture of local SSD-based storage and remote Object storage.

### The current approach has various side-effects:

1. There is a non-trivial cost in increasing your data ingest as clusters need to be scaled and more SSD storage & IOPs need to be provided

2. The choice needs to be made between hot and cold data, and also what is archived. Now your data is in 2-3 different places and queries can be fast or slow depending on where the data is

The end result is a user of these existing solutions would need to carefully consider all data that is ingested, and put limits and or sampling to control the devops and cost burden.

### Axiom was built from the ground-up to tackle this issue in a few ways:

1. Decouple ingest and querying pipelines

2. Build a stateless ingest pipeline that requires minimal compute/memory to storage as much as 1.5/day per vCPU

3. Ingest all data into Object Storage, enabling the cheapest storage possible for all ingested data

4. Enable querying scale-out with cloud functions, requiring no constantly-running servers just waiting for a query to be processed. Instead, go from zero-to-infinity querying instantly

### The benefits of our approach are:

1. The most efficient ingestion pipeline for massive amounts of data

2. Allow storing more data for less by exclusively using inexpensive Object Storage for all data

3. Query data that’s 10 milliseconds or 10 years old at any time

4. Reduce the Total Cost of Ownership of your log management and analytics pipelines with simple scale and maintenance that Axiom provides

5. Free your organization to do more with it’s data.


## How long can I retain data for with Axiom?

At Axiom, we believe that organizations should have access to all their data, all of the time.

And so, paid versions of Axiom allow for unlimited retention with no limits on the time window of data you can query.


## Can I trial Axiom inside my organization?

Yes! If you would like to get a full trial of Axiom for your organization, please request a trial and we’ll get you up and running in no time!


## How is Axiom licensed?

Axiom is licensed on an annual basis via a software license key provided to your organization via sales.
||||||| 09ff13e
=======
<div class="axi-header">
  <h1>Frequently Asked Questions</h1>
</div>

This page includes frequently asked questions from users which we feel help to build a better understanding of Axiom and how best to use it. If you cannot find an answer to your own questions, please do not hesitate to [contact us](mailto:support@axiom.co).

## What is Axiom?

Axiom is log management and analytics solution that reduces the cost and management overhead of logging as much data as you want.

With Axiom, organizations no longer need to choose between their data and their costs. Axiom has been built from the ground-up to allow for highly efficient data ingestion and storage, and then a zero-to-infinite query scaling that allows you to query all your data, all the time.

Organizations use Axiom for continuous monitoring & observability, as well as an event store for running analytics and deriving insights from all their event data.

Axiom consists of a datastore and a user-experience that work in tandem to provide a completely unique log-management & analytics experience.

## Where does Axiom run?

Axiom is a self-host software product that runs right inside of your infrastructure. Your infrastructure can be cloud VPCs or metal, Axiom can be run anywhere.

Axiom only requires a Postgresql database and an object store to run. There is no requirement for Apache Kakfa, Zookeeper, or any other dependency that would be a headache to maintain.

AWS S3, Azure, Google Cloud, DigitalOcean, Minio, and Ceph are all supported object stores and so Axiom is at home almost anywhere.


## Is there an Axiom Cloud?

Not at this moment, but it is coming soon (Q1 2021). If you would like to register your interest, then please sign up below to be notified:


<script charset="utf-8" type="text/javascript" src="//js.hsforms.net/forms/shell.js"></script>
<script>
  hbspt.forms.create({
	portalId: "7714395",
	formId: "b959af05-de2b-4177-9d26-f785874416b8"
});
</script>


## How is Axiom different than other logging solutions?

At Axiom, our goal is that no organization has to ignore or delete a single piece of data no matter its source: logs, events, frontend, backends, audits, etc.

We found that existing solutions would place restrictions on how much data can be collected either on purpose or as a side-effect of their architectures.

For example: the “state of the art” in logging is running stateful clusters that need shared knowledge of ingestion and will use a mixture of local SSD-based storage and remote Object storage.

### The current approach has various side-effects:

1. There is a non-trivial cost in increasing your data ingest as clusters need to be scaled and more SSD storage & IOPs need to be provided

2. The choice needs to be made between hot and cold data, and also what is archived. Now your data is in 2-3 different places and queries can be fast or slow depending on where the data is

The end result is a user of these existing solutions would need to carefully consider all data that is ingested, and put limits and or sampling to control the devops and cost burden.

### Axiom was built from the ground-up to tackle this issue in a few ways:

1. Decouple ingest and querying pipelines

2. Build a stateless ingest pipeline that requires minimal compute/memory to storage as much as 1.5/day per vCPU

3. Ingest all data into Object Storage, enabling the cheapest storage possible for all ingested data

4. Enable querying scale-out with cloud functions, requiring no constantly-running servers just waiting for a query to be processed. Instead, go from zero-to-infinity querying instantly

### The benefits of our approach are:

1. The most efficient ingestion pipeline for massive amounts of data

2. Allow storing more data for less by exclusively using inexpensive Object Storage for all data

3. Query data that’s 10 milliseconds or 10 years old at any time

4. Reduce the Total Cost of Ownership of your log management and analytics pipelines with simple scale and maintenance that Axiom provides

5. Free your organization to do more with it’s data.


## How long can I retain data for with Axiom?

At Axiom, we believe that organizations should have access to all their data, all of the time.

And so, paid versions of Axiom allow for unlimited retention with no limits on the time window of data you can query.


## Can I trial Axiom inside my organization?

Yes! If you would like to get a full trial of Axiom for your organization, please request a trial and we’ll get you up and running in no time!


## How is Axiom licensed?

Axiom is licensed on an annual basis via a software license key provided to your organization via sales.
>>>>>>> master
||||||| 09ff13e
=======
<div class="axi-header">
  <h1>Frequently Asked Questions</h1>
</div>

This page includes frequently asked questions from users which we feel help to build a better understanding of Axiom and how best to use it. If you cannot find an answer to your own questions, please do not hesitate to [contact us](mailto:support@axiom.co).

## What is Axiom?

Axiom is log management and analytics solution that reduces the cost and management overhead of logging as much data as you want.

With Axiom, organizations no longer need to choose between their data and their costs. Axiom has been built from the ground-up to allow for highly efficient data ingestion and storage, and then a zero-to-infinite query scaling that allows you to query all your data, all the time.

Organizations use Axiom for continuous monitoring & observability, as well as an event store for running analytics and deriving insights from all their event data.

Axiom consists of a datastore and a user-experience that work in tandem to provide a completely unique log-management & analytics experience.

## Where does Axiom run?

Axiom is a self-host software product that runs right inside of your infrastructure. Your infrastructure can be cloud VPCs or metal, Axiom can be run anywhere.

Axiom only requires a Postgresql database and an object store to run. There is no requirement for Apache Kakfa, Zookeeper, or any other dependency that would be a headache to maintain.

AWS S3, Azure, Google Cloud, DigitalOcean, Minio, and Ceph are all supported object stores and so Axiom is at home almost anywhere.


## Is there an Axiom Cloud?

Not at this moment, but it is coming soon (Q1 2021). If you would like to register your interest, then please sign up below to be notified:


<script charset="utf-8" type="text/javascript" src="//js.hsforms.net/forms/shell.js"></script>
<script>
  hbspt.forms.create({
	portalId: "7714395",
	formId: "b959af05-de2b-4177-9d26-f785874416b8"
});
</script>


## How is Axiom different than other logging solutions?

At Axiom, our goal is that no organization has to ignore or delete a single piece of data no matter its source: logs, events, frontend, backends, audits, etc.

We found that existing solutions would place restrictions on how much data can be collected either on purpose or as a side-effect of their architectures.

For example: the “state of the art” in logging is running stateful clusters that need shared knowledge of ingestion and will use a mixture of local SSD-based storage and remote Object storage.

### The current approach has various side-effects:

1. There is a non-trivial cost in increasing your data ingest as clusters need to be scaled and more SSD storage & IOPs need to be provided

2. The choice needs to be made between hot and cold data, and also what is archived. Now your data is in 2-3 different places and queries can be fast or slow depending on where the data is

The end result is a user of these existing solutions would need to carefully consider all data that is ingested, and put limits and or sampling to control the devops and cost burden.

### Axiom was built from the ground-up to tackle this issue in a few ways:

1. Decouple ingest and querying pipelines

2. Build a stateless ingest pipeline that requires minimal compute/memory to storage as much as 1.5/day per vCPU

3. Ingest all data into Object Storage, enabling the cheapest storage possible for all ingested data

4. Enable querying scale-out with cloud functions, requiring no constantly-running servers just waiting for a query to be processed. Instead, go from zero-to-infinity querying instantly

### The benefits of our approach are:

1. The most efficient ingestion pipeline for massive amounts of data

2. Allow storing more data for less by exclusively using inexpensive Object Storage for all data

3. Query data that’s 10 milliseconds or 10 years old at any time

4. Reduce the Total Cost of Ownership of your log management and analytics pipelines with simple scale and maintenance that Axiom provides

5. Free your organization to do more with it’s data.


## How long can I retain data for with Axiom?

At Axiom, we believe that organizations should have access to all their data, all of the time.

And so, paid versions of Axiom allow for unlimited retention with no limits on the time window of data you can query.


## Can I trial Axiom inside my organization?

Yes! If you would like to get a full trial of Axiom for your organization, please request a trial and we’ll get you up and running in no time!


## How is Axiom licensed?

Axiom is licensed on an annual basis via a software license key provided to your organization via sales.
>>>>>>> master
