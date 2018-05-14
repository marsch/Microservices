<p align="center">
  <img src="https://github.com/openintegrationhub/Microservices/blob/master/Assets/medium-oih-einzeilig-zentriert.jpg" alt="Sublime's custom image" width="400"/>
</p>

The revolution in data synchronization — the Open Integration Hub enables simple data synchronization between any software applications and thus accelerates digitalisation

Visit the official [Open Integration Hub homepage](https://www.openintegrationhub.de/)

# Microservices

## Table of Content
<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Table of Content](#table-of-content)
- [Introduction](#introduction)
- [Contribution](#contribution)
	- [Contribution Guidelines](#contribution-guidelines)
	- [Code of Conduct](#code-of-conduct)
- [Contact](#contact)
- [Content](#content)
	- [Folders](#folders)
	- [Documents](#documents)
- [Workgroup](#workgroup)
	- [Information](#information)
	- [Member](#member)
		- [OIH APIs](#oih-apis)
		- [Secure Access Control](#secure-access-control)
		- [Repository Management](#repository-management)
		- [Message Processing](#message-processing)
		- [Management Services](#management-services)
- [Wording](#wording)
- [Contribution](#contribution)

<!-- /TOC -->

## Introduction

This repository contains all developing tasks considering the finalisation of the OIH api integration platform prototype,  including the
core components "Integration Services" and "Data Hub".  Additionally, this repository includes the development of the microservices and the primary purpose is to develop the platform prototype as the basis for further use.

## Contribution
### Contribution Guidelines
Before you contribute please read our [contribution guidelines](CONTRIBUTING.md).

### Code of Conduct

To see how members of the community are expected to behave, please read the [code of conduct](CODE_OF_CONDUCT.md). We apply the code of conduct defined by the Contributor Covenant, which is used across many open source projects, such as [NodeJS](https://github.com/nodejs/node), [Atom](https://github.com/atom/atom) and [Kubernetes](https://github.com/kubernetes/kubernetes).

## Contact
When looking for further information or support, please contact: philipp.hoegner@cloudecosystem.org.

## Content

The following illustration shows how the microservices are aggregated within the workgroups:

![Microservice Workgroups](https://github.com/openintegrationhub/Microservices/blob/master/Assets/OIHWorkgroupContent.png)

### Folders

- [ManagementServices](ManagementServices): Contains all concepts for management services such as logging and monitoring, reporting and analytics
- [MessageProcessing](MessageProcessing): Includes all descriptions regarding message processing, communication router, scheduler and the resource coordinator
- [OihAPIs](OihAPIs): Describes the Open Integration Hub REST-APIs i.e. integration framework api and smart data framework api, which allows corresponding  managing of the OIH platform
- [Protocols](Protocols): Collection of all taken protocols
- [RepositoryManagement](RepositoryManagement): Contains all repository service concepts such as Integration Component- and Content Repository
- [SecureAccessControl](SecureAccessControl): Includes microservices to manage secure access. This includes the Identity-, User- and Secure-Key-Management

### Documents

- [CONTRIBUTING](CONTRIBUTING.md): Contains the contribution guideline
- [DataHub](DataHub.md): Describes the concept of the smart data framework, using adapters/ transformer and a smart data framework adapter
- [InfrastructureAndTechnologies](InfrastructureAndTechnologies.md): Lists the technologies used in the OIH and the motivation behind them
- [IntegrationServices](IntegrationServices.md): Includes an overview of the intergration framework services as well as a short description for each microservice. It describes the integration into the kubernetes environment with message oriented middleware as the basis for communication
- [MicroserviceDescriptionTemplate](MicroserviceDescriptionTemplate): Gives a brief overview of what a microservice description should look like  
- [MicroserviceOverview](MicroserviceOverview.md): Table of all integration framework microservices with their company in charge and the official deadline
- [TestingTools](TestingTools.md): Table of possible testing tools with their main feautures

## Workgroup
### Information
- Each workgroup has at least one **status call** every two weeks
- **Every Committer** must attend the status call
- The governance model defines the workgroup members' roles into managers, committers or contributors

### Member

#### OIH APIs
|Member Name |GitHub Alias|Company| Role |
| --- | --- | --- | --- |
| Igor Drobiazko  |[drobiazko](https://github.com/drobiazko)|[Elastic.io](https://www.elastic.io/)| **Manager**  |
| Selim Achmerzaev |[sachmerz](https://github.com/sachmerz)|[Basaas](https://www.basaas.com/app-store)| Committer  |
| Philipp Hoegner|[philecs](https://github.com/philecs)|[Cloud Ecosystem](http://www.cloudecosystem.org/)| Committer |
| Pavel Nedelko|[pnedelko](https://github.com/pnedelko)|[Elastic.io](https://www.elastic.io/)| Contributor|

#### Secure Access Control
|Member Name |GitHub Alias|Company| Role |
| --- | --- | --- | --- |
| Selim Achmerzaev |[sachmerz](https://github.com/sachmerz)|[Basaas](https://www.basaas.com/app-store)| **Manager**  |
| Igor Drobiazko  |[drobiazko](https://github.com/drobiazko)|[Elastic.io](https://www.elastic.io/)| Committer  |
| Philipp Hoegner|[philecs](https://github.com/philecs)|[Cloud Ecosystem](http://www.cloudecosystem.org/)| Committer |
| Lutz Ashauer |[lashauer](https://github.com/lashauer)|[StoneOne](http://stoneone.de)| Contributor  |
| Falk Voigt |[falkvoigt](https://github.com/falkvoigt)|[Basaas](https://www.basaas.com/app-store)| Contributor  |
| Hans Eggert |[heggert](https://github.com/heggert)|[Basaas](https://www.basaas.com/app-store)| Contributor  |
| Pavel Nedelko|[pnedelko](https://github.com/pnedelko)|[Elastic.io](https://www.elastic.io/)| Contributor|

#### Repository Management
|Member Name |GitHub Alias|Company| Role |
| --- | --- | --- | --- |
| Igor Drobiazko  |[drobiazko](https://github.com/drobiazko)|[Elastic.io](https://www.elastic.io/)| **Manager**  |
| Selim Achmerzaev |[sachmerz](https://github.com/sachmerz)|[Basaas](https://www.basaas.com/app-store)| Committer  |
| Hansjörg Schmidt  |[hschmidthh](https://github.com/hschmidthh)|[Wice](https://wice.de/)| Committer  |
| Philipp Hoegner|[philecs](https://github.com/philecs)|[Cloud Ecosystem](http://www.cloudecosystem.org/)| Committer |
| Lutz Ashauer |[lashauer](https://github.com/lashauer)|[StoneOne](http://stoneone.de)| Contributor  |
| Susanne Braun |[brausu](https://github.com/brausu)|[Fraunhofer IESE](https://www.iese.fraunhofer.de/)| Contributor  |
| Shterion Yanev | [spyanev](https://github.com/spyanev) |[Wice](https://wice.de/)| Contributor  |
| Pavel Nedelko|[pnedelko](https://github.com/pnedelko)|[Elastic.io](https://www.elastic.io/)| Contributor|

#### Message Processing
|Member Name |GitHub Alias|Company| Role |
| --- | --- | --- | --- |
| Igor Drobiazko  |[drobiazko](https://github.com/drobiazko)|[Elastic.io](https://www.elastic.io/)| **Manager**  |
| Selim Achmerzaev |[sachmerz](https://github.com/sachmerz)|[Basaas](https://www.basaas.com/app-store)| Committer  |
| Philipp Hoegner|[philecs](https://github.com/philecs)|[Cloud Ecosystem](http://www.cloudecosystem.org/)| Committer |
| Susanne Braun |[brausu](https://github.com/brausu)|[Fraunhofer IESE](https://www.iese.fraunhofer.de/)| Contributor  |
| Shterion Yanev | [spyanev](https://github.com/spyanev) |[Wice](https://wice.de/)| Contributor  |
| Hansjörg Schmidt  |[hschmidthh](https://github.com/hschmidthh)|[Wice](https://wice.de/)| Contributor  |
| Pavel Nedelko|[pnedelko](https://github.com/pnedelko)|[Elastic.io](https://www.elastic.io/)| Contributor|

#### Management Services
|Member Name |GitHub Alias|Company| Role |
| --- | --- | --- | --- |
| Selim Achmerzaev |[sachmerz](https://github.com/sachmerz)|[Basaas](https://www.basaas.com/app-store)| **Manager**  |
| Igor Drobiazko  |[drobiazko](https://github.com/drobiazko)|[Elastic.io](https://www.elastic.io/)| Committer  |
| Philipp Hoegner|[philecs](https://github.com/philecs)|[Cloud Ecosystem](http://www.cloudecosystem.org/)| Committer |
| Lutz Ashauer |[lashauer](https://github.com/lashauer)|[StoneOne](http://stoneone.de)| Contributor  |
| Shterion Yanev | [spyanev](https://github.com/spyanev) |[Wice](https://wice.de/)| Contributor  |
| Pavel Nedelko|[pnedelko](https://github.com/pnedelko)|[Elastic.io](https://www.elastic.io/)| Contributor|
| Falk Voigt |[falkvoigt](https://github.com/falkvoigt)|[Basaas](https://www.basaas.com/app-store)| Contributor  |
| Hans Eggert |[heggert](https://github.com/heggert)|[Basaas](https://www.basaas.com/app-store)| Contributor  |

## Wording

Within the project different terms and abbreviations are frequently used. All terms and abbrevations are explained within the [glossary](https://github.com/openintegrationhub/Connectors/wiki/Glossary) and our [list of abbrevations](https://github.com/openintegrationhub/Connectors/wiki/Abbreviations).

## Contribution

Before you contribute, please read the [contribution guideline](https://github.com/openintegrationhub/microservices/blob/master/CONTRIBUTING.md).
