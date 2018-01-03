# Logging & Monitoring

Under the hood of the Integration Hub is a Kubernetes cluster used to run
all the Docker containers of internal micro-services and all the integration
flows. The easiest logging method for containerized applications is to
write to the standard output and standard error streams.

In Kubernetes one can implement cluster-level logging by installing a
logging agent on each node. The logging agent is a container that has
access to a directory with log files from all of the application containers
on that node and pushes these logs to a logging backend, such as [Elasticsearch](https://www.elastic.co/).
The following diagram demonstrates node-level logging architecture in Kubernetes.

![Node-level logging architecture](Assets/k8s-logging-with-node-agent.png)


Kubernetes provides two optional logging agents: Stackdriver Logging for
use with Google Cloud Platform and Elasticsearch. Both agents are using
[Fluentd](https://www.fluentd.org) behind the scenes. Because applications
might exists across multiple Kubernetes nodes, a logging agent must run
on every node. This is ensured by a [DaemonSet](https://kubernetes.io/docs/admin/daemons/).
Fluentd provides [Docker image](https://github.com/fluent/fluentd-kubernetes-daemonset)
to deploy Fluentd as DaemonSet to gather all the logs from all the applications
on all Kubernetes nodes.

The Fluentd DaemonSet can be configured to send the logs to [Elasticsearch](https://www.elastic.co/)


