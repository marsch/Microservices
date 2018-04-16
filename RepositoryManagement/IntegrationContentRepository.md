# Integration Content Repository

# 1. Introduction

This document describes the evaluation of the Microservice "Integration Content Repository".
This microservice is part of the integration services of the Open Integration Hub.

# 2. Description

## 2.1. Purpose of the Microservice Integration Content Repository

If we talk about "content" here, we mean "flows". All connected solutions and to the
Open Integration Hub and the work they are doing there are represented by an "integration flows".
A data modification in one of the affected systems should propagate to all connected solutions / systems
as defined in the corresponding integration flows.

The integration flows are defined by a single user of the Open Integration Hub or a
member of an organization which uses the Open Integration Hub.

These flows have to be stored, retrieved, updated and deleted. The Integration Content Repository
will provide these functionabilities.

## 2.2. Requirements for the Integration Content Repository

We will need a component within the Open Integration Hub which fulfill the following user stories.

| User story: | As a user I want to store an integration flow for a specific integration task |
| :--- | :--- |

| User story: | As a user I want to retrieve the integration flows of a specific user |
| :--- | :--- |

| User story: | As a user I want to update the integration flows of a specific user |
| :--- | :--- |

| User story: | As a user I want to delete the integration flows of a specific user |
| :--- | :--- |

| User story: | As a user I want to retrieve a specific integration flows by its id |
| :--- | :--- |

This will lead to the following use cases:

| Label        | USE CASE - Store Integration Flow |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes adding a new integration flow |
| **Trigger:** | A user wants to store a new integration flow |
| **Preconditions:** | Credentials for the user are given |
| **Main Success Scenario:** | Added integration flow |
| **Failure Scenario:** | Adding new flow was not successful |
| **Basic Workflow:** | 1. Define user <br/> 2. Define flow <br/> 3. Store flow  |
| **Alternative Workflow:** | 1a. User is unknown 2a. Incorrect flow defined <br/> 3a. Throw error   |

| Label        | USE CASE - Retrieve Integration Flow |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes retrieving a given integration flow |
| **Trigger:** | A user wants to retrieve an integration flow |
| **Preconditions:** | Credentials for the user are given |
| **Main Success Scenario:** | Flow retrieved |
| **Failure Scenario:** | Retrieving the flow was not successful |
| **Basic Workflow:** | 1. Define user <br/> 2. Define flow <br/> 3. Retrieve flow  |
| **Alternative Workflow:** | 1a. User is unknown 2a. Incorrect flow defined <br/> 3a. Throw error   |

| Label        | USE CASE - Update Integration Flow |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes updating a given integration flow |
| **Trigger:** | A user wants to update an integration flow |
| **Preconditions:** | Credentials for the user are given |
| **Main Success Scenario:** | Flow updated |
| **Failure Scenario:** | Updating the flow was not successful |
| **Basic Workflow:** | 1. Define user <br/> 2. Define flow <br/> 3. Retrieve flow  |
| **Alternative Workflow:** | 1a. User is unknown 2a. Incorrect flow defined <br/> 3a. Throw error   |

| Label        | USE CASE - Delete Integration Flow |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes deleting a given integration flow |
| **Trigger:** | A user wants to delete an integration flow |
| **Preconditions:** | Credentials for the user are given |
| **Main Success Scenario:** | Flow deleted |
| **Failure Scenario:** | Updating the flow was not successful |
| **Basic Workflow:** | 1. Define user <br/> 2. Define flow <br/> 3. Retrieve flow  |
| **Alternative Workflow:** | 1a. User is unknown 2a. Incorrect flow defined <br/> 3a. Throw error   |

As described in the document identity management (s. [SecureAccessControl/Identity Management.md](../SecureAccessControl/IdentityManagement.md))
the OIH consists of multiple services and agents with different roles and authorization. These roles and their authorizations have to be considered.

# 3. Concept of the Integration Content Repository

As described in the document integration services (s. [/IntegrationServices.md](../IntegrationServices.md))
the Integration Content Repository is positioned between the Scheduler and the Resource Coordinator.

The Scheduler helps to perform the polling of the integration flows periodically.
The Resource Coordinator enforces every tenant to comply with the defined policies on resource sharing.

The communication with the other microservices within the OIH is done via an API (to be specified).

The flows are specified in JSON, therefore we store and retrieve them in JSON. The JSON-Format of the flows
has to be specified.

The following requests can be done:
- Retrieve all flows: Returns all flows belonging to the given user.
If the user is a member of an organization, all the flows of the organization are returned.
If the user is a member in multiple organizations, the given authentication is used to match the proper organization.
- Retrieve a flow by id: Returns the flow with the given ID.
- Store new flow: Returns the stored given flow.
- Update flow by id: Returns the updated given flow.
- Delete flow by id: Return the id of the deleted given flow.

# 4. Technologie Used 

Storing, updating and retrieving the JSON-flows could be done in a simple GIT-Repository. This is can be simple implemented.
