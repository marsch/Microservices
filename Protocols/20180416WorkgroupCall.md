# Protocol
**Attendees**: Selim, Igor, Hansjörg, Frank, Jürgen, Philipp, Dennis <br>
**Absent**: -

## Status update
### Basaas
- [Identity and Access Management description](../SecureAccessControl/IAMConcept.md) has been finished
- Rudimental authentication / user management exists
  - Dedicated server for authentication & user management
- Swagger documentation will be provided for the (micro-)services
- Authorization is currently missing
  - Suggestion is to use [attribute enhanced role based access control](../SecureAccessControl/AccessControlManagement.md#attribute-based-access-control)
  - For the first draft existing roles by _elastic.io_ will be used
  - Roles will possibly be extended by further roles
  - Roles will be used as a set of attributes
: OpenID connect provided is initially implemented
  - Open source library is used
  - The open source libary will possibly be extended by personal extensions

### Elastic.io
- Currently none of the services is acutally ready
- Because of the amount of services and their interdependence, the progress is slow (but steady)
- Currently working on the Integration Content Repository, Message-Oriented-Middleware, Scheduler and Resource Coordinator
- Message-Oriented-Middleware is not a service but more like an instance of RabbitMQ
- Container must be able to communicate with RabbitMQ
- In a first version the services provided by _elastic.io_ will be without a REST API
- Current descriptions can not be expanded but old descriptions can be adjusted to new microservice description format

### Wice
- Waiting for feedback on the [Integration Content Repository](../RepositoryManagement/IntegrationContentRepository.md)
- Feedback has to be incorporated into the existing descriptions and afterwards _wice_ will start the actual implementation of the Integration Content Repository
- First ideas/thoughts on CRUD Monitoring

## Descriptions
- [Microservice Description Template](../MicroserviceDescriptionTemplate.md) provided by Philipp, will be used for the microservice descriptions
    - Template is only the first draft
    - Template may change over time

## Findings

- Code will be pushed till the 30.06.2018 by **Basaas**
- In approximately one month a first usable version of the service will be provided **Elastic.io**

## Derived Tasks
- [ ] Set up a regular call for wednesday at 11:00 (First call will be moved to 23.04.2018) **Philipp**
- [ ] Send discussion point about microservice interface description technology to Franz for architecture call **Philipp**
- [ ] Provide description of Integration Content Repository (till 23.04.2018) **Hansjörg**
- [ ] Provide description of CRUD Monitoring **Hansjörg**
- [ ] Adjust current microservice descriptions ([LoggingMonitoring](../ManagementServices/LoggingMonitoring.md), [CommunicationRouter](../MessageProcessing/CommunicationRouter.md), [MessageOrientedMiddleware](../MessageProcessing/MessageOrientedMiddleware.md), [SchedulerAndResourceCoordinator](../MessageProcessing/SchedulerResourceCoordinator.md), [IntegrationComponentRepository](../RepositoryManagement/IntegrationComponentRepository.md) and [SecureKeyManagement](../SecureAccessControl/SecureKeyManagement.md)) **Igor**
- [ ] Provide description about usage (incl. reasoning) of _Kubernetes_, _Docker_ and _NodeJS_ **Selim / Falk**
