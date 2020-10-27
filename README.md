# eureka-naming-server

This is a test project for eureka naming server between many microservices
The other microservices (currency-exchange-service, currency-conversion-service and limits service) knowing the service URL which they should call from the eureka naming server 

# Example URLs

http://localhost:8761/
Eureka server URL

# Port
Used port is 8761

# Summary
This project is part from some projects created for testing microservice cloud. Those projects are
- spring-cloud-config-server

This service load the configuration for the microservices from repository on github called microservice-config and expose it as web services to be called by other microservices

- eureka naming server

This is a naming server to register the microservices on it to be able to
retrieve the URLs for different microservices by microservice name which defined inside application.properties file

- zuul-api-gateway-server

This is a gateway server to handle the authentication/authorization and the communication between microservices.
This project is created without implementing the business for authentication/authorization for testing.
This service register itself in eureka naming server.
The API gateway know the services URLs which should be called for each request from the eureka naming server.
This service register  the requests tracing by zipkins and rabbitMQ.

- limits-service

This service used to test loading configuration from spring-cloud-config-server. It is also used to test the hystrix and resilience circle breaker for fault tolerance
This service register itself in eureka naming server.

- currency-exchange-service

This service used to test the rest template, feign rest client, rubbon client load balancer. It callect the currency exchange rate information from external API
This service register itself in eureka naming server.
This service register  the requests tracing by zipkins and rabbitMQ.

- currency-conversion-service

This service used to call the currency-exchange-service to get the currency exchange rate.
This service created to test the rest template, feign rest client, rubbon client load balancer.
This service register itself in eureka naming server.
This service register  the requests tracing by zipkins and rabbitMQ.

Tested inside those projects:
- JPA
- Spring cloud configuration server read from git repository
- Rest template
- Feign rest client 
- Ribbon client load balancer
- Eureka naming server
- Zuul api gateway
- Spring cloud sleuth to add unique ID to logs
- Zipkin distributed tracing system using Rabbit MQ [required rabbitMQ and zipkin to be running]
- Hystrix and resilience circle breaker for fault tolerance.

