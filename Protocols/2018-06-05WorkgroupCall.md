# Protocol
**Attendees**: Selim, Igor, Hansjörg, Franz, Dennis <br>
**Absent**: Philipp

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

# Topics

- [Status MVP - Status Elastic.io](#status-mvp---status-elasticio)
- [Microservice APIs](#microservice-apis)
- [SDF API discussion*](#sdf-api-discussion)
- [Description Review](#description-review)
- [Status update](#status-update)
	- [Basaas](#basaas)
	- [Wice](#wice)
			- [Content Integration Repository](#content-integration-repository)
- [Organistory](#organistory)
- [Derived Tasks](#derived-tasks)


<!-- /TOC -->

---

# Status MVP - Status Elastic.io
* Elastic has finalized the implementation of MVP
   * Igor is going to test this implementation until Friday (08.06.2018) and, if there are no issues, commit/publish the code on Github

# Microservice APIs
* Franz: To achieve a loosely coupled communication between microservices, the idea of an ESB (message bus) should be evaluated

# SDF API discussion*
  * Franz: small services can be synchronous, but a chain of service calling other service should be designed in an asynchronous manner, e.g. a message is acknowledged synchronous and added to a queue. Other services can process the message async.
   * Igor: Similar to Integration Framework one may need both world – synchronous (REST) as asynchronous (Queue). SDF can have a synchronous REST API, generate a transaction id and acknowledge the request. Internally, the data could be further transformed, de-duplicated, etc. fully asynchronous. The caller shouldn’t have to wait until the data is fully processed.
   * REST-API: Igor will modify the current Swagger draft Yaml of SDF API until 08.06.2018. The working group will work out the SDF API on the basis of this draft.

# Description Review
* Everyone: will fill out the missing parts of the template

# Status update
## Basaas
- API Documentation: [Swagger Doku](https://account.basaasdev.de/api-docs/ )

## Wice
#### Content Integration Repository
* Wice will document their current state until 08.06.2018
* The service is being developed in Node.js and a Swagger API documentation will be provided

# Organistory
 * Working group accepts the proposal to append the Architecture Workgroup call as follow up to the microservices call on Wednesdays

# Derived Tasks
- [ ] Review adjusted microservice descriptions and add missing content. See issue: [Review adjusted descriptions](https://github.com/openintegrationhub/Microservices/blob/master/Protocols/2018-05-16WorkgroupCall.md#boards?repos=110119585) **Igor, Hansjörg, Selim**
- [ ] The working group should specify the criteria when to use REST and when to use the Message Queue
- [ ] Franz will document the discussed ideas in the Architecture Decisions document
- [ ] Modify the current Swagger draft Yaml of SDF API until 08.06.2018
