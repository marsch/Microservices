# 4. Scenarios for IAM in OIH

## Summary
this Document will show 5 different scenarios how to setup and handle Authentication, authorization and Usermanagement in the OIH Project. We will not workflows here. For detailed view on it we provide some more papers.

It's needed to define one of the scenarios as useable to have a clear picture how authorisation is done within OIH.

### Scenario 1 : primitive Service account definition
in this scenario we have 1 master account ( create, edit and delete Service account). That master account is only for managing the Service account and there Jobs, it can't be used to make own Jobs.

Service account is in the same time the abstraction of the tenant itself. There is no additional information about the tenant and the user related to that Account

### Scenario 2 : master/service and tenant account definition
The master account is the same as of Scenario 1. 

Tenant account is an addition to the Service Account of Scenario 1, the difference is that here we have some tenant related information saved within OIH so that we can create some use statistics.


 ![Scenario 1-2](https://github.com/openintegrationhub/Microservices/blob/master/SecureAccessControl/assets/Scenario1-2.png)




### Scenario 3 : master/service, tenant and user account definition with Access Control handled by tenant
The master account is the same as of Scenario 1.

The tenant account is the same as of Scenario 1 but will also get a member list of it's users and access controll for booked solutions.

The user accounts have to be related to 1 specific Tenant and only basic user informations are saved (username, full name, email). On that we could do more detailed statistics could be done.

### Scenario 4 : master/service, tenant and user account definition with Access Control handled by user
The master account is the same as of Scenario 1.

The tenant and user account is the same as of Scenario 3 but the access control will be per user. What we achieve is a basic but better separation of Departments or concerns.

example: salesforce is used by controlling and accounting and they should not use the same credentials and accounts in salesforce

 ![Scenario 2-4](https://github.com/openintegrationhub/Microservices/blob/master/SecureAccessControl/assets/Scenario2-4.png)


### Scenario 5: master/service, tenant and user account definition combined with Groups (with Access Control)
The master account is the same as of Scenario 1.

The tenant and user account is the same as of Scenario 3 but we add Groups with access controll connected to it. This enables us to create access control based on Departments directly without having duplicated access controll on User.

Also it provides metrics about which Department of the Tenant is using which Job's and how often.

![Scenario 5](https://github.com/openintegrationhub/Microservices/blob/master/SecureAccessControl/assets/Scenario5.png)