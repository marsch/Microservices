# Protocol
**Attendees**: Hansjörg, Igor, Philipp, Dennis <br>
**Absent**: Selim <br>

## Status update
### Basaas
- 

### Elastic.io
- Because of team internal issues no progress was made within the last week
- MVP will be published in approximately 3 weeks

### Wice
- Working on Integration Content Repository

## Adjustment Overview
Some of the planned microservices are not needed anymore. Therefore the [microservice overview](https://github.com/openintegrationhub/Microservices/blob/master/IntegrationServices.md) needs to be updated.
Furthermore the still needed microservices need to be reconsidered, i.e. if their scope is still the same.

In addition, the short descriptions within the overview must be expanded, i.e. all missing description needs to be added. Currently: [CRUD Monitoring](https://github.com/openintegrationhub/Microservices/blob/master/ManagementServices/CRUDMonitoring.md) and [Identity and Access Management](https://github.com/openintegrationhub/Microservices/blob/master/SecureAccessControl/IAMConcept.md) missing.


- **Communication Router**: routing to different messaging queues. Act as proxy between Kubernetes services & messaging queues

- **Integration Component Repository**: Installation of docker registry with docker images. Integration Components with docker files. Or optional a cloud registry für open source co.mponents. This microservice will provide an interaface which is able to look up which component lies within which registry

## OIH APIs
All participants agreed to collect needed operations within the [OIH API description](https://github.com/openintegrationhub/Microservices/tree/master/OihAPIs)

Basic ideas provided by Selim:

``` markdown
- Management API
   - Mandanten & User Management (IAM)
- Management von Connectoren
    - Teams
    - Repositories
    - Versioning
- Workflow
    - Flows managen
    - Flow Events (streaming api?)

- Inter-Connector / Integration-Framework Datenaustausch
    - SDK (Queue unter der Haube)
- Smart Data Framework
    - Anbindung an IAM via REST, wenn neue Entitäten (z.B. Tenants) angelegt werden?
        - Mandanten anlegen —> in SDF neue Elemente anlegen?
    - SDF Adapter
        - CRUD Operationen auf SDF (Entity anlegen, auslesen, modifizieren, etc.)
            - Kann SDK basiert sein und unter der Haube REST nutzen?

Zu klärende Fragen:
- Welche Operationen werden mit großer Wahrscheinlichkeit asynchron sein?
```

## Tasks
### Last Call
- [ ] Review Swagger API by Basaas **Igor**
- [ ] Review CRUD Monitoring documentation **Igor** + **Selim**
- [ ] Extend [infrastructure and technology](https://github.com/openintegrationhub/Microservices/blob/master/InfrastructureAndTechnologies.md) description by MongoDB part **Selim**
- [ ] Extend [infrastructure and technology](https://github.com/openintegrationhub/Microservices/blob/master/InfrastructureAndTechnologies.md) description by RabbitMQ part **Igor**

--> All tasks still open (See [derived tasks](#derived-tasks))

### Derived Tasks
- [ ] Review Swagger API by Basaas **Igor**
- [ ] Review CRUD Monitoring documentation **Igor** + **Selim**
- [ ] Extend [infrastructure and technology](https://github.com/openintegrationhub/Microservices/blob/master/InfrastructureAndTechnologies.md) description by MongoDB part **Selim**
- [ ] Extend [infrastructure and technology](https://github.com/openintegrationhub/Microservices/blob/master/InfrastructureAndTechnologies.md) description by RabbitMQ part **Igor**
- [ ] Collect needed operations that need to be provided by the API within the OIH API description **Selim**, **Hansjörg** & **Igor**
- [ ] Bring up discussion point of "short description" in the [integration service](https://github.com/openintegrationhub/Microservices/blob/master/IntegrationServices.md) file wihtin the next workgrou call **Philipp**
