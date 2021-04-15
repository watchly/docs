<div class="axi-header">
  <h1>Ingesting via Kubernetes</h1>
</div>

You can ingest logs from your Kubernetes cluster into **Axiom** using filebeat.

The following is an example of a **DaemonSet** configuration to ingest your data logs into **Axiom**. 


## Configuration

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: filebeat
  namespace: kube-system
  labels:
    k8s-app: filebeat
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: filebeat
  labels:
    k8s-app: filebeat
rules:
- apiGroups: [""] # "" indicates the core API group
  resources:
  - namespaces
  - pods
  verbs:
  - get
  - watch
  - list
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: filebeat
subjects:
- kind: ServiceAccount
  name: filebeat
  namespace: kube-system
roleRef:
  kind: ClusterRole
  name: filebeat
  apiGroup: rbac.authorization.k8s.io
---
apiVersion: v1
data:
  filebeat.yml: |-
    filebeat.autodiscover:
      providers:
        - type: kubernetes
          node: ${NODE_NAME}
          hints.enabled: true
          hints.default_config:
            type: container
            paths:
              - /var/log/containers/*${data.kubernetes.container.id}.log

    processors:
      - add_cloud_metadata:

    output.elasticsearch:
      hosts: ['${AXIOM_HOST}/api/v1/datasets/${AXIOM_DATASET_NAME}/elastic']
      api_key: 'axiom:${AXIOM_INGEST_TOKEN}'
    setup.ilm.enabled: false
kind: ConfigMap
metadata:
  annotations: {}
  labels:
    k8s-app: filebeat
  name: filebeat-config
  namespace: kube-system
---
apiVersion: apps/v1
kind: DaemonSet
metadata:
  labels:
    k8s-app: filebeat
  name: filebeat
  namespace: kube-system
spec:
  selector:
    matchLabels:
      k8s-app: filebeat
  template:
    metadata:
      annotations: {}
      labels:
        k8s-app: filebeat
    spec:
      containers:
        - args:
            - -c
            - /etc/filebeat.yml
            - -e
          env:
            - name: AXIOM_HOST
              value: http://axiom:80
            - name: AXIOM_DATASET_NAME
              value: dataset
            - name: AXIOM_INGEST_TOKEN
              value: xait-xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
            - name: NODE_NAME
              valueFrom:
                fieldRef:
                  apiVersion: v1
                  fieldPath: spec.nodeName
          image: docker.elastic.co/beats/filebeat-oss:7.9.3
          imagePullPolicy: IfNotPresent
          name: filebeat
          resources:
            limits:
              memory: 200Mi
            requests:
              cpu: 100m
              memory: 100Mi
          securityContext:
            runAsUser: 0
          terminationMessagePath: /dev/termination-log
          terminationMessagePolicy: File
          volumeMounts:
            - mountPath: /etc/filebeat.yml
              name: config
              readOnly: true
              subPath: filebeat.yml
            - mountPath: /usr/share/filebeat/data
              name: data
            - mountPath: /var/lib/docker/containers
              name: varlibdockercontainers
              readOnly: true
            - mountPath: /var/log
              name: varlog
              readOnly: true
      dnsPolicy: ClusterFirst
      restartPolicy: Always
      schedulerName: default-scheduler
      securityContext: {}
      serviceAccount: filebeat
      serviceAccountName: filebeat
      terminationGracePeriodSeconds: 30
      volumes:
        - configMap:
            defaultMode: 416
            name: filebeat-config
          name: config
        - hostPath:
            path: /var/lib/docker/containers
            type: ""
          name: varlibdockercontainers
        - hostPath:
            path: /var/log
            type: ""
          name: varlog
        - hostPath:
            path: /var/lib/filebeat-data
            type: ""
          name: data
  updateStrategy:
    rollingUpdate:
      maxUnavailable: 1
    type: RollingUpdate
```

--- 

### Configure env

In the above configuration, 

Configure your environment variables 

```yaml
env:
            - name: AXIOM_HOST
              value: http://axiom:80
            - name: AXIOM_DATASET_NAME
              value: dataset
            - name: AXIOM_INGEST_TOKEN
              value: xait-xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

Where:

- **AXIOM_HOST** is your Axiom deployment URL. 
- **AXIOM_DATASET_NAME** is your dataset name. 
- **AXIOM_INGEST_TOKEN** This can be either your ingest token or personal token. 

The personal token can be retrieved from the users profile page **(Setting > Profile > Personal token)** 

or an ingest token retrieved from the **settings > Ingest Token** page of your  Axiom deployment.


The personal access token grants access to all resources available to the user, while the ingest token just allows ingestion into the datasets the token is configured for.

---

- After editing your values, apply the changes to your cluster using **`kubectl apply -f daemonset.yaml`**