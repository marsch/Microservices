# Communication Router

An execution of an integration flow is always started by the 1st step of the flow, the so called `trigger`. A trigger
component used to monitor changes in the source system and start the flow upon detecting any changes. The detection of
changes may occur in active or passive way, depending on the trigger type:

* `polling` trigger: actively monitoring the source service in predefined intervals
* `webhook` trigger: waiting for the source system to send notification about changes

In order to receive webhook requests, an integration flow with a webhook trigger needs a externally-reachable URL.
This URL must be unique to the flow and must not change when the flow is restarted due to an error or an user action.
For each of the webhooh flows a [Service](https://kubernetes.io/docs/concepts/services-networking/service/) is created
in Kubernetes.

A webhook flow work in 2 modes:

* `asynchronous`: the flow's pods are started on-demand whenever a webhook requests comes in. These pods are mortal [Jobs](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/), they exit once the flow completed data processing. Such flows can be used for an asynchronous processing where not response to a webhook request is required.
* `synchronous`: flow's pods are [Deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)  running at any given time. Such flows can easily create a response to the incoming request as they have zero latency to start up the pods.
