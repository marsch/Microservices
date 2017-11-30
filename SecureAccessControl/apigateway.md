# Api Gateway

This document describes the evaluation of Api Gateways within the Open Integration Hub.

## Why is Api Gateways necessary?

it's common practice to have only 1 Endpoint in each Client. That helps to redeploy and changes Api's without downtime or Client release. 


## Types of API Gateway architecture

there are 2 different Type's of API Gateways. Which are simply the same as a Proxy  from/to a Service. 

### Type1: ###
common usage (simply 1 Proxy for all API requests) the job is only to abstract the over Api's behind. That kind of Api Gateway could be handled from nearly every Proxy you could imagine (Apache, Nginx, Varnish ...)

![ApiGateway1](https://github.com/openintegrationhub/Microservices/blob/master/SecureAccessControl/assets/ApiGateway1.png)

Pros: easy to manage, in a Kubernetes Cluster a Ingress Controller could do that job.,  small footprint and easy to scale.
Cons: there is a need for the things the Fat Gateway could do which needs to be implemented on Service side or like Caching handled via CDN ...

### Type2: ###

i would call it Fat Api Gateway. It could do more than just Proxy request like Authentication, Autorisation, WAF Functions, Caching. that is just an Extension to what the common type can do so the normal Proxy is still needed.
Exampels: Nginx Plus, Varnish, Kong, apiumbrella, Tyk

![ApiGateway2](https://github.com/openintegrationhub/Microservices/blob/master/SecureAccessControl/assets/ApiGateway2.png)

Pros: a lot of features (Cache, Auth, Autor. , WAF)
Cons: most of the Examples are not Open Source, a need for Know how for management


## Link Collection

[Api Gateway done by Nginx](https://www.nginx.com/blog/building-microservices-using-an-api-gateway/)  
[Api Gatewas done by Kong](https://getkong.org/#comparison)  
[Api Gateway principles](http://microservices.io/patterns/apigateway.html)  
[Modern Authentication flows](https://nordicapis.com/how-to-control-user-identity-within-microservices/)  
[Kubernetes how too Authenticate](https://medium.com/jeroen-rosenberg/from-monolith-to-microservice-architecture-on-kubernetes-part-2-authentication-with-jwt-934ea030923)  




## Challenges

1.  the Type and or component to choose depends on what is more possible to        achieve. implementation of needed features or managing a 3rd Party Software. 