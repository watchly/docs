<div class="axi-header">
  <h1>Runing Axiom on Kubernetes</h1> 
</div>

The best way to get Axiom running on Kubernetes is by using our [Helm chart](https://github.com/axiomhq/axiom-helm-charts).

The following documentation assumes some knowledge of working with Kubernetes and Helm charts.

If you would like further help or installation in a different environment, please  [contact support](mailto:support@axiom.co).


## Add the Axiom Helm Repository

```
$ helm repo add axiom https://axiomhq.github.io/axiom-helm-charts
$ helm repo update
$ # just to check
$ helm search repo axiom
NAME       	CHART VERSION	APP VERSION	DESCRIPTION  
axiom/axiom	0.2.3        	1.3.0-rc.8 	Axiom Private
```


## Create `values.yaml`

The latest version of `values.yaml` can be found [in the github repository](https://github.com/axiomhq/axiom-helm-charts/blob/master/values.yaml).

```yaml
# Values file for axiom.
# This is a YAML-formatted file.

# License token (as provided by console.axiom.co)
licenseToken: ""

# [required] Postgres endpoint, should be in the following format:
# "postgresql://host:port/dbname?user=[username]&password=[pwd]&sslmode=require"
# the postgres user provided must be able to create new tables in the DB
postgresUrl: ""

# [required] URL specifying how to send emails:
# "sendgrid://apikey?from=noreply@domain.org&fromName=name"
emailUrl: ""

# URL of this instance, email notifications will use this to link back
# "https://my-axiom.company.org"
externalUrl: ""

# Definition of storage
storage:
  primary:
    # [required] Set to a URI based on the cloud you're using, we support azure / aws / do / gcp
    # Azure: "blob://container"
    # AWS: "s3://bucketName"
    # DigitalOcean: "spaces://bucketName"
    # GCP: "gcs://bucketName"
    # The URI can optionally be suffixed by a path prefix (for example "s3://bucketName/path/prefix")
    #uri: "s3://axiom"

    # AWS-specific properties
    #awsRegion: 'us-east-1'
    #awsAccessKeyID: ''
    #awsSecretAccessKey: ''

    # Azure-specific properties
    #azureStorageAccount: ''
    #azureStorageAccessKey: ''

    # DigitalOcean-specific properties
    #spacesRegion: 'nyc3'
    #spacesKey: ''
    #spacesSecret: ''

    # GCP-specific properties
    #googleApplicationCredentials: '{
    #  "type": "service_account",
    #  "project_id": "...",
    #}'

  fallback:
    # Fallback storage is used when primary is not reachable
    # use the same format as primary storage including credentials
    uri: ""

ingress:
  enabled: false
  annotations:
    {}
    # kubernetes.io/ingress.class: nginx
    # kubernetes.io/tls-acme: "true"
  hosts:
    - host: my-axiom.local
      paths: ["/*"]
  tls: []
  #  - secretName: my-axiom-tls
  #    hosts:
  #      - my-axiom.local

# Settings for axiom-core
core:
  replicas: 3
  resources:
    requests:
      cpu: 250m
      memory: 256Mi
    # limits:
    #   cpu: 500m
    #   memory: 1Gi
  podAnnotations: {}
  nodeSelector: {}
  tolerations: []
  affinity: {}

# Settings for axiom-db
db:
  replicas: 3
  resources:
    requests:
      cpu: 750m
      memory: 2Gi
    # limits:
    #   cpu: 2000m
    #   memory: 4Gi
  podAnnotations: {}
  nodeSelector: {}
  tolerations: []
  affinity: {}

# Settings for axiomdb-query-fn
queryFn:
  replicas: 4
  resources:
    requests:
      cpu: 500m
      memory: 256Mi
    # limits:
    #   cpu: 2000m
    #   memory: 1Gi
  podAnnotations: {}
  nodeSelector: {}
  tolerations: []
  affinity: {}

```

## Install Axiom Using Helm

Once your `values.yaml` has been filled out, you can finally install Axiom in your Kubernetes cluster using the following commands:

```yaml
helm upgrade -i -f values.yaml my-axiom axiom/axiom
```


## Support

If you are having trouble runnnig Axiom, please [get in touch via the Slack community or email](https://axiom.co/support), and we'll help you get going as fast as possible!
