# Authentication handling in Microservice Environment #

## There are some more Methods to do that.

* 1.Authentication Service is generating Tokens and is also the Endpoint to validate the Token. Used Technologie is Oauth2.

Pros: One Service to do all the Authentication related work (no shares of Key's or Persistence)
Cons: Single Point of failure, higher Network Traffic load for Communication

* 2.Authentication Service is generating Tokens (example: JWT)  and the validation is done from each service. Used Technologie is Oauth2 with JWT

Pros: split workload and reduce Network Traffic
Cons: there is a shared Lib and a shared Secret which needs to be maintained

* 3.Authentication Service is generating Tokens (example: JWT)  and the validation is done from Api Gateway. Used Technologie is Oauth2 with JWT

Pros: Validation is done on first level of the hosting
Cons: managing fat api Gateway not all a open source

## Technologies for WEB Applications ##

besause all of the given technologies are standards i will only point on a summary side how it works.

* Oauth2  
 [Oauth2-simplified](https://aaronparecki.com/oauth-2-simplified/)

* Oauth2 with JWT  
[JWT](https://jwt.io/introduction/)

* SAML2.0  
[SAMl2.0](http://saml.xml.org/saml-specifications)


## Link Collection

[Modern Authentication flows](https://nordicapis.com/how-to-control-user-identity-within-microservices/)  
[Kubernetes how too Authenticate](https://medium.com/jeroen-rosenberg/from-monolith-to-microservice-architecture-on-kubernetes-part-2-authentication-with-jwt-934ea030923)  

## Challenges

1.  the Type and or component to choose depends on what is more possible to        achieve. implementation of needed features or managing a 3rd Party Software. 