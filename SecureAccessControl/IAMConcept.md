Introduction
============

Identity and Access Management (short: IAM) is one of the core components in OIH which is needed to provide a secure authentication and authorization of users/clients. Further features of an IAM system are user and roles management as well as audit logging.

  

Description
===========

This document will describe all needed features to handle Authentication, Authorization and User management in OIH.

Throughout this document, we will also look into different setups and approaches of using IAM in OIH, starting from simple feature list and moving forward to more extensive and complex examples:

*   Basic/minimal approach with simple tokens (JWT)
*   Advanced approach with an external identity provider and SSO (OpenId Connect)

  

  

Technologies used
=================

[JWT](https://jwt.io/)

[OpenId Connect](http://openid.net/connect/)

[OAuth 2.0](https://oauth.net/2/)

  

Basic IAM setup
===============

This approach aims at a very basic and simple operation of OIH using only a minimal set of microservices. We assume a scenario where an individual or a company uses OIH in the intranet without the need for external identity providers and using a simple authentication and authorization mechanisms.

The basic parameters of this setup are:

*   Authentication is a dedicated service (AuthService)
*   Authorization mechanisms are either part of the said AuthService or is a utility library integrated into a separate gateway or microservice
*   Use of HS256 or HS512 symmetric encryption with a strong secret key

  

We also assume that in a basic use case there isn't necessary a user interface for the OIH. And although the OIH does provide a REST-API, the client is most likely to be _curl_, _Postman_ or some other (Micro)-Service interacting with the REST-API. The later could make use of an OAuth Library and thus have an easy way to use access and refresh tokens. But in the case of using _curl_ or _Postman_, it would be more convenient and easy to have a long living JWT access token (e.g. with an expiration time of 1h) without the need to refresh the token every few minutes. This of course comes at the cost of risks when using long living tokens similar to those risks when using solely Basic Authentication.

> The AuthService is intended to support both cookie and Authorization Header based authentication. In case of a browser, the AuthService will set the JWT as a cookie and automatically prolong it, if the user makes a HTTP request to the AuthServer before the JWT expires.

  

Identity Store
--------------

For a basic setup we will be using a MongoDB with Passport.js to store and authenticate users. Account management is done by the AuthService. 

In a more advanced approach, one could use LDAP or Active Directory as an identity store.

> If no other information except a unique identifier of the user (e.g. user_id) is needed, we can store all user data (e.g. Name, E-Mail) in the AuthService. Should this data also be required in other microservices as well, for example for data aggregation, performance, etc., then we will have to introduce an identity/user provisioning mechanism. This provisioning mechanism would allow synchronization and merging of user data in all affected services. A very simplified solution for user provisioning could be accomplished through the message queue – all subscribes are notified with new data set, when an account has been modified. The subscribers can then merge/import the data into their own system. Same goes for the de-provisioning.

  

  

Authorization and Roles
-----------------------

The precise role definitions of OIH may change at a later stage, for the sake of simplicity, we will use the current state of roles and privileges of elastic.io platform, which are _Admin_, _Organization-User_ and _Organization-Admin_.

*   A user can be part of more than one organization and can have different roles in each of her organizations
*   An Admin can manage organizations
*   Organization-User can create and start her own flows and organization flows (organization flows are accessible for all organization users, but each user may have their own private flows)
*   Organization-Admin can do everything what Organization-Users can do, plus manage her organization data and Organization-Users (invite, change role, remove from organization)

  
![Users and Identities in OIH](./assets/users_in_oih.png)


User management
---------------

In contrast to a more tenant centric user management where a user can only be assigned to a single tenant, we propose a user centric IAM. This means that users can be created in OIH and can be assigned to more than one organization/tenant and have different roles in each organization. Every user can edit her personal data and password individually. The current [elastic.io](http://elastic.io) platform adopts a similar approach.

The Admin can create organizations, create/invite users and assign them to an organization, whereas an Organization-Admin can only invite users to her organization or exclude them from it.

  

Authentication and authorization flows
--------------------------------------

The following diagram visualizes a simple authentication flow from a client perspective.

![Authentication in OIH](./assets/oihIamConcept.png)

  

The client either has an access token (JWT) or will be redirected to the AuthService for authentication. The authentication can be a simple username + password process, returning the JWT token. The client has to save this token and use it in the Authorization Bearer header for all future requests. 

The access token is a JWT token which contains at least the following data:

*   user_id
*   username
*   firstname
*   lastname
*   roles – an array of objects, containing organization_id and the role name within that organization

  

As mentioned earlier, a user can be part of more than one organization, which is why we propose the use of context, similar to the context of kubernetes. Upon authentication, the client can fetch all contexts which it has, e.g.:

```bash
curl -i https://heimdal.example-oih.com/api/v1/context \
  -H "Authorization: Bearer mytoken123"
```

This will return the list of contexts the client/user is assigned to, e.g.:

```javascript
[
  {
    "org": "some-org-id-1",
    "role": "ORG_ADMIN"
  },
  {
    "org": "some-org-id-2",
    "role": "USER"
  }
]
```

The cient an then choose the desired role and will receive a new JWT containing the claims for that specific context:

```bash
curl -X POST -i https://heimdal.example-oih.com/api/v1/context/some-org-id-1 \
  -H "Authorization: Bearer mytoken123"
```

Corresponsing JWT payload:

```javascript
{
  "sub": "1234567890",
  "name": "John Doe",
  "role": "ORG_ADMIN",
  "org_id": "some-org-id-1"
}
```

The advantage of setting a context is that, the underlying services can focus on the current user role and her current tenant/ogranization without knowledge of 1 to n relationsgip between a user and organizations.

The Gateway in this diagram is representative for any other gatekeeper module or service. Due to the fact that OIH consists of many services, it would be an obvious choice to have the authentication and authorization validation in one module or service and limited to one distrinct location instead of distributing it accross many services and thus requiring the synchronization/updates at many points. We will view the alternatives in the advanced examples.

The core idea of this basic approach is to validate the token at gateway level and pass the token as an HTTP-Header to the services behind the gateway. These service can react to the claims, assuming that these cannot have been tampered with if the request has passed the gateway. Different approaches are possible in order for the gateway to validate the token:

* Gateway and AuthService share a secret
	* Gateway does not have to communicate with the AuthService
    * Changing the secret must be propagated to AuthService and Gateway
* Gateway uses the public JWS key from AuthService to validate the tokens
    * See the JWS documentation for details 
* Gateway calls the AuthService to validate a token and caches that token (or the "jti"-Id of a JWT) for a short time

  

For a very simple and basic scenario, we will be using the first approach with a shared secret.

This basic scenario does not deal with token revocation, which is why the tokens might be long living (at least 1 hour). Upon expiry, the user needs to re-authenticate to receive a new access token.

  

List of supported Methods and Routes
------------------------------------

| endpoint        | method           | description  | comments |
| ------------- |:-------------:| -----|------|
| /healthcheck | GET | Returns 200 OK when Service is up | Could be used for Kubernetes and liveliness checks |
| /login | POST | Returns 200 and a JWT. <br>JWT ist returned and additionally set as a cookie. The JWT Token is used to authenticate to other Services | JWT can have role information in it |
| /logout | POST | Returns a 200 OK and will remove the corresponding cookie(s) |  |



Connectors and external services
--------------------------------

Specific connectors like Adapters can have read/write access to the Smart Data Framework API (short: SDF). The OIH is a multi-tenant environment, which is why there should also be means to limit the data a connector can access.

Given the fact that a separate Docker container is launched for each component of an integration flow, we could generate an access token for each connector on start-up. Such access tokens will contain the current tenant/organization id and allow the SDF to enforce it's authorization mechanisms. 

>**Important notice**
We refrain from generating refresh tokens and create the access tokens for connectors without an expiration time.

>Typically, refresh tokens are stored by an AuthService permanently and do not change. This would mean, that we would need to create a separate refresh token for each connector on start-up and to delete that refresh token when the connector shuts down. Any given connector may crash, hang, be manually or atomatically restarted, the OIH plattform could have an unexpected outage, etc. If the AuthService should store refresh tokens, there there should be a mechanism or a dedicated daemon in the OIH, which instructs the AuthService to remove old refresh tokens.

>From a security perspective, the sole purpose of this connector access token is to access OIH internal services like SDF. In this environment, we do not see the risk of leaking a long-living access token greater than the risk of leaking a long-living refresh token.

  

  

  

  

Advanced setup
==============

In a more complex scenario we will make use of an external identity provider on OpenId Connect basis (e.g. Basaas Marketplace) to authenticate with the OIH.

Other mentionable difference to the basic setup are:

*   Use of RS265 or RS512 for assymetric encryption
*   JWT is signed using the private key from AuthService
*   Gateway can validate the authenticity of the JWT signature using the public from AuthService

  

IAM in context of OIH and microservices
---------------------------------------

In a microservice architecture like the OIH a client (or a service on behalf of a user) can communicate to multiple other services. In terms of multi-tenancy, we require a sophisticated authorization, for example allowing access only to those integration flows and credentials the current user is actually eligibile for. As described in the basic scenario, our approach is to make use of signed JWT tokens containing the claims/grants of the user/client. The following example illustrates the access to credentials store.

![Authentication in OIH](./assets/authorization_types.png)

Flow:

1.  Client authenticates
2.  Client receive the JWT containing the claims and current context
3.  Client accesses the credentials for org1 in OIH. Gateway validates, that the JWT is valid.
4.  Credentials Service can either use
    1.  a middleware/library to verify that the client is authorized to access the ressource (business logic within credentials service)
    2.  or make a request to the authorization service, which maps all authorization policies

**TODO** > Our preferred version ist the use of middleware for authorization and an attriibute based access control (ABAC). 

The validation of JWT can be done by the Gateway, but also by any service/module, which has access to the JWS public key of the AuthService. 

### Authorization

For the OIH, we consider the authorization within each microservice as the best alternative:

*   We have a very limited set of roles and applying rules and also a low number of APIs accessible from outside (currently only two: Integration Framework and Smart Data Framework)
*   A seperate authorization policy service would require much coordination within different working groups
*   Each microservice could have their own interpretation of what an specific combination of user role and attributes mean

All these points could lead to inconsistent policies when managing them all at one point instead of doing it in the dedicated services.

Single Sign-On
--------------

There are scenarios, for example in context of the Basaas marketplace, where we want the identity provider to be outside of OIH and allow the users to login into OIH using their external credentials. We will use OpenId Connect to achieve this.

Authentication in the context of a generic ecosystem
----------------------------------------------------

In this section we will define a concept for user authentication to OIH inside a generic ecosystem. It utilizes OpenID Connect ([http://openid.net/specs/openid-connect-core-1_0.html](http://openid.net/specs/openid-connect-core-1_0.html)) which extends the OAuth2 protocol ([https://tools.ietf.org/html/rfc6749](https://tools.ietf.org/html/rfc6749)). The core idea is to just authenticate the user and separate this process from authorization.

  

### Authentication Flow

![Authentication in OIH](./assets/Authentication-steps.png)

  

This abstract flow illustrates the interaction between the three roles and includes the following steps:

  

(precondition) A registered account containing a valid OIH-uid is required. A registration can be accomplished in different ways and is beyond the scope of this section.

(A) User requests an action. For example a request can be made to reorganize clients or to connect a new one. Since OIH is Relying Party ([http://openid.net/specs/openid-connect-core-1_0.html#Authentication](http://openid.net/specs/openid-connect-core-1_0.html#Authentication)) it starts authenticating the User by initializing OpenID Connect flow. 

(B) OIH sends an authentication request (AuthN) to specified OpenID Provider. The HTTP request parameter "response\_type" has value "id\_token", so it corresponds to implicit flow according to the specifications ([http://openid.net/specs/openid-connect-core-1\_0.html#id\_tokenExample](http://openid.net/specs/openid-connect-core-1_0.html#id_tokenExample)).

(C) If User is not already authenticated, he will be forwarded to a specific login page.

(D)Once he logged in and has been authenticated, the OpenID Provider creates Id-token (JWT) and redirects User to OIH with token stored in the HTTP header.

(E*) After Id-token signature is validated User is authenticated and OIH computes initial request (A)..

  

This authentication flow brings several benefits. It relies on established standards so a future implementation will be covered by detailed documentation. In addition, Users get an interface that should already be known to them, since large providers (e. g. maintained by Google or Facebook) have been around for a couple of years.

