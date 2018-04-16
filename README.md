# Introduction

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

- `Management Services:` Contains the architectural logging and monitoring concept
- `MessageProcessing`: Includes all descriptions regarding message processing, communication router, scheduler and the                        resource coordinator
- `OihAPIs`: Describes the REST-APIs for the Basaas Master Service Account, which allows corresponding  managing of the OIH platform
- `RepositoryManagement`: Contains the Integration Component- and Content Repository descriptions, additionally, the evaluation of these are summarized, including the purpose, requirements, concept and technologies used
- `SecureAccessControl`: Includes the Identity-, User- and Secure-Key-Management for managing the credentials

#### Documents

- `CONTRIBUTING`: Contains the contribution guideline
- `DataHub`: Describes the data flow from a source adapter to a target adapter, crossing the transformer in the middle to transform the data so it is possible to use a peer-to-peer integration
- `IntegrationServices`: Includes all hub micro-services and their integration into the kubernetes environment with message oriented middleware as the basis for communication

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
