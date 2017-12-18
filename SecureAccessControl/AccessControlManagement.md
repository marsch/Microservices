
# Access Control Management

## Summary
this is a summary about all different types of Access Control and illustrates the Pros & Cons of access control models which are suitable for OIH. Literature links will be provided at the end of the page. For every IAM system the Access Control is a crucial part beside the Identity Management (User Management). 

**Access Control delivers four services**

* authorization
* authentication
* access approval
* accountability


## Access Control Models
There is a huge list for different types of Access Control Models, for example:

Here the list of different Access Control Models   
Basic (Department of Defense 1960 / 1970):  

* MAC (Mandatory Access Control)
* DAC (Discretionary Access Control) 

**Common**:

* RBAC (Role Based Access Control)
* ABAC (Attribute Based Access Control)
    * policy-based access control (PBAC)
    * claims-based access control (CBAC)
* IBAC (Identity Based Access Control)

**Specials**:

* HBAC (History Based Access Control)
* OrBAC (Organization Based Access Control)
* IBAC (Identity Based Access Control)
* RAC (Rule Based Access Control)
* Responsibility Based Access control


In this Document we will focus on models which are common in Microservices and Web Application Use cases.



### Role Based Access Control:

This Model uses individual designed roles to decide about access. The design of the roles requires a fundamental analysis of the target organization and/or use cases.

For Example a normal Organization structure (simplified without hierarchy for example purpose):  C-Level, Sales, Controlling, User, Administrator

**Advantages**:

* easy to map Org structure to Access Roles
* well known handling in use and administration
* widespread usage 

**Disadvantages**:

* Documentation of Roles needs to be on point
* Multi-tenancy is difficult to implement and makes administration much more complex
* user could have different groups which contain different Roles which overrules each other
* In worst case: introduce new roles which contains subsets access privileges of multiple other roles


### Attribute Based Access Control
This model is based on policies which are related on combined attributes (Subject attributes, Resource attributes, Environment attributes, Action attributes). The main difference between ABAC and RBAC is that policies are not needed to be pre-defined und could be created when a use case (feature) is created, because the needed attributes are already in place. ABAC provides dynamic, context-aware and risk-intelligent access control.



**core Architecture**:

* PEP: Policy Enforcement Point is responsible for protecting apps/data. PEP inspects request for access and generates a authorization request for PDP. 
* PDP: Policy Decision Point is the logic behind ABAC and decides if the authorization request is approved or not. Therefore it uses all given information and missing information where requested from PIP.
* PIP: Policy Information Point provides Information from external resources like LDAP and DB

**Policies example**:

1. A user can view a document if the document is in the same department as the user
2. A user can edit a document if they are the owner and if the document is in draft mode
3. Deny access before 9am


**Advantages**:

* easy to map Org structure to attributes
* widespread usage in modern technologies
* Multi-tenancy could be handled via attributes

**Disadvantages**:

* more complex implementation because of decision making to gather infomation
 
 
Links to Literature


https://en.wikipedia.org/wiki/Access_control  
https://www.owasp.org/index.php/Access_Control_Cheat_Sheet#tab=Role_Based_Access_Control__28RBAC_29  
https://www.axiomatics.com/attribute-based-access-control/  
http://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-162.pdf  
http://blog.identityautomation.com/rbac-vs-abac-access-control-models-iam-explained  
https://en.wikipedia.org/wiki/Attribute-based_access_control  
https://en.wikipedia.org/wiki/Discretionary_access_control  
https://en.wikipedia.org/wiki/Mandatory_access_control  
