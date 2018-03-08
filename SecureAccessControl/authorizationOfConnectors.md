# Authorization of Connectors

## Summary
This document shows the authorization flow of Connectors to the OIH environment in two different scenarios. There are two different setups to get a look on it, first the connector is living OIH environment and the secondly the connector is related to the ISV environment.

The possible technics for the authorization is shown in a different document. Dependencies for the flow will be identified but not detailed.



## Dependencies

*  authorization service
*  secret store
*  Graph to build a picture of all booked services
    * a tenant will have abstractions of it's different identities in each ISV
    *  each abstraction will have it's own secrets it's used for connector to OIH communication
    *  the root tenant could have more than 1 secret related to the Chosen Authentication Scenario
*  kind of Gateway


## Scenarios for connector setup


the only thing different in the 2 Setups is where the Gateway for authentication/authorization needs to be installed.

IMPORTANT: the below Diagrams shows that authorization is handled by each Platform 


 ![Connector Scenario 1](https://github.com/openintegrationhub/Microservices/blob/master/SecureAccessControl/assets/ConnectorScenario1.png)


 ![Connector Scenario 2](https://github.com/openintegrationhub/Microservices/blob/master/SecureAccessControl/assets/ConnectorScenario2.png)

