# Integration Hub Micro-Services

![Integration Hub Microservices](Assets/IntegrationHubMicroservices.png)


## Integration Component (Adapter) Repository

The integration components are lightweight and stand-alone Docker images that include everything needed to run the
component, including the component's code, a runtime, libraries and dependencies. The component images are stored in an
[Integration Component Repository](./IntegrationComponentRepository.md).

## Scheduler and Resource Coordinator

There are two ways to trigger a flow execution: to poll changes periodically or to receive notifications through webhooks.
The majority of integration flows poll perform polling as the most of APIs out there don't support webhooks. The polling
is performed periodically with the help of the *Scheduler*.

Because Integration Hub is a multi-tenant environment, it is theoretically possible that some tenants cause starvation
of others through an unfair usage of shared resources. The *Resource Coordinator* enforces  every tenant to comply with
the defined policies on resource sharing.

Please read more details on [Scheduler and Resource Coordinator](./SchedulerResourceCoordinator.md).

## Communication Router

In contrast to polling a flow can be started by an external event. Modern APIs provide support for webhooks in order to
avoid wasting of resources when polling. The external system can be configured with a webhook url to be called upon
changes in the external system. The *Communication Router* is used to expose externally-reachable URLs for integration
flows that can be used to implement webhook-triggered flows. These URLS may be registered in external systems to sent
notifications to. See more details on [Communication Router](./CommunicationRouter.md).

## Logging & Monitoring

Integration Hub micro-services and integration flows are running in a Kubernetes
cluster. Read details on [cluster-level logging architectures](./LoggingMonitoring.md).

## Message Oriented Middleware

All the communication between steps of an integration flow in runtime is happening through a message broker. Two steps
of an integration flow are separate Docker container isolated from each other. They are connected through a messaging
queue than provides them a reliable and asynchronous communication protocol. See more details on [Message Oriented Middleware](./MessageOrientedMiddleware.md).

## Secure-Key-Management

An integration flow defines how data flow between various external systems and how these data are transformed between
steps of that flow. However an integration flow does not define how to connect to these external systems. An integration
can be considered as a clonable template that must not contain any sensible user data, such as API credentials. The API
credentials are stored in the [Secure-Key-Management](SecureKeyManagement.md).

## Integration Content Repository
TBD