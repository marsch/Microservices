# Authentication/Authorisation handling in Microservice Environment #

## Technologies for WEB Applications ##

### Authorisation ###

* [Oauth2](https://aaronparecki.com/oauth-2-simplified/)   
Authentication Service is generating Tokens and is also the Endpoint to validate the Token. Used Technologie is Oauth2.  
Pros: One Service to do all the Authentication related work (no shares of Key's or Persistence)  
Cons: Single Point of failure, higher Network Traffic load for Communication

* [Oauth2 with JWT](https://jwt.io/introduction/)  
Authentication Service is generating Tokens (example: JWT)  and the validation is done from each service. Used Technologie is Oauth2 with JWT  
Pros: split workload and reduce Network Traffic  
Cons: there is a shared Lib and a shared Secret which needs to be maintained

### Authentication ###

* [OpenID Connect](http://openid.net/connect/)  
Protocoll Suite for Authentication & SSO based on OAuth2.0  
Pros: Small payload, highly optimised for WEB Applications  
Cons: Authorisation is handeled by OAuth2.0 (you need OpenID Connect and OAuth2.0)

### Authorisation & Authentication ###

* [SAMl2.0](http://saml.xml.org/saml-specifications)  
XML based Standard for exchange Authentication & Authorisation Data to archive Single Sign On (SSO), Federation and Identity Management  
Pros: data transfer is free to use (SOAP, HTTP, JMS ...), combine both Authentication and Authorisation  
Cons: XML payload (assertions) very Big

## Usecases and Findings ##

1. Authentication and Authorisation from enduser  

* that case is not a part from OIH because only APIs are communicating

2. Authorisation from APIs

* for that case it's common practice to use OAuth2.0 and if the environment is APP or WebApp also in combination with JWT 

## Link Collection

[Modern Authentication flows](https://nordicapis.com/how-to-control-user-identity-within-microservices/)  
[Kubernetes how too Authenticate](https://medium.com/jeroen-rosenberg/from-monolith-to-microservice-architecture-on-kubernetes-part-2-authentication-with-jwt-934ea030923)  
[Differents between SAML & OpenID Connect](https://www.gluu.org/blog/oauth-vs-saml-vs-openid-connect/)  
[UMA user managed access](https://www.gluu.org/resources/documents/standards/uma/)

## Challenges

1.  the Type and or component to choose depends on what is more possible to achieve. implementation of needed features or managing a 3rd Party Software. 