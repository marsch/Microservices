<p align="center">
  <img src="https://github.com/openintegrationhub/Microservices/blob/master/Assets/medium-oih-einzeilig-zentriert.jpg" alt="Sublime's custom image" width="400"/>
</p>

The revolution in data synchronization — the Open Integration Hub enables simple data synchronization between any software applications and thus accelerates digitalisation 

# Microservices

## Table of Content
- [Introduction](#introduction)

- [Content](#content)
  - [Folders](#folders)
  - [Documents](#documents)

- [Workgroup](#workgroup)
  - [Information](#information)
  - [Member](#member)

- [Wording](#wording)

- [Contribution](#contribution)

## Introduction

This repository contains all developing tasks considering the finalisation of the OIH api integration platform prototype,  including the
core components "Integration Services" and "Data Hub".  Additionally, this repository includes the development of the microservices and the primary purpose is to develop the platform prototype as the basis for further use.

## Content

The following illustration shows how the microservices are aggregated within the workgroups:

![Microservice Workgroups](https://github.com/openintegrationhub/Microservices/blob/master/Assets/OIHWorkgroupContent.png)

#### Folders

- `ManagementServices`: Contains all concepts for management services such as logging and monitoring, reporting and analytics
- `MessageProcessing`: Includes all descriptions regarding message processing, communication router, scheduler and the                        resource coordinator
- `OihAPIs`: Describes the Open Integration Hub REST-APIs i.e. integration framework api and smart data framework api, which allows corresponding  managing of the OIH platform
- `Protocols`: Collection of all taken protocols
- `RepositoryManagement`: Contains all repository service concepts such as Integration Component- and Content Repository
- `SecureAccessControl`: Includes microservices to manage secure access. This includes the Identity-, User- and Secure-Key-Management

#### Documents

- `CONTRIBUTING`: Contains the contribution guideline
- `DataHub`: Describes the concept of the smart data framework, using adapters/ transformer and a smart data framework adapter
- `InfrastructureAndTechnologies`: Lists the technologies used in the OIH and the motivation behind them
- `IntegrationServices`: Includes an overview of the intergration framework services as well as a short description for each microservice. It describes the integration into the kubernetes environment with message oriented middleware as the basis for communication
- `MicroserviceDescriptionTemplate`: Gives a brief overview of what a microservice description should look like  
- `MicroserviceOverview`: Table of all integration framework microservices with their company in charge and the official deadline
- `TestingTools`: Table of possible testing tools with their main feautures

## Workgroup
#### Information
- Each workgroup has at least one **status call** every two weeks
- **Every Committer** must attend the status call
- The governance model defines the workgroup members' roles into managers, committers or contributors


#### Member

**Workgroup overarching manager:** Igor Drobiazko

| Workgroup  | Member Name | Role |
| ------------- | ------------- | ------------- |
| OIH APIs  | Igor  | **Manager & Committer**  |
|  | Selim  | Committer  |
|  | Philipp  | Committer  |
|  | Pavel | Contributor|
| (Secure) Access Control | Selim  | **Manager & Committer**  |
|  | Lutz  | Committer  |
|  | Igor  | Committer  |
|  | Philipp  | Committer |
|  | Falk  | Contributor  |
|  | Hans  | Contributor  |
|  | Pavel | Contributor|
|  Repository (Management)| Igor  | **Manager & Committer**  |
|  | Lutz  | Committer |
|  | Selim | Committer  |
|  | Susanne  | Committer  |
|  | Philipp | Committer  |
|  | Shterion  | Contributor  |
|  | Hansjörg  | Contributor  |
|  | Pavel | Contributor |
| Message Processing | Igor  | **Manager & Committer**  |
|  | Selim  | Committer  |
|  | Susanne  | Committer  |
|  | Philipp  | Committer  |
|  | Shterion  | Contributor  |
|  | Hansjörg  | Contributor  |
|  | Pavel | Contributor |
| Management Services | Selim  | **Manager & Committer**  |
|  | Igor  | Committer  |
|  | Lutz  | Committer  |
|  | Philipp  | Committer  |
|  | Shterion  | Contributor  |
|  | Pavel | Contributor |
|  | Falk  | Contributor  |
|  | Hans  | Contributor  |

## Wording

Within the project different terms and abbreviations are frequently used. All terms and abbrevations are explained within the [glossary](https://github.com/openintegrationhub/Connectors/wiki/Glossary) and our [list of abbrevations](https://github.com/openintegrationhub/Connectors/wiki/Abbreviations).

## Contribution

Before you contribute, please read the [contribution guideline](https://github.com/openintegrationhub/microservices/blob/master/CONTRIBUTING.md).
