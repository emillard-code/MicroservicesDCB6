Purpose of each microservice application:

MicroserviceDCB1:
Provides a basic Department model class.
Also has basic controller, repository and service classes.

MicroserviceDCB2:
Provides a basic User model class (as well as an in-built Department class).
Also has basic controller, repository and service classes.
Has a ResponseTemplateVO class that enables application to interact with Department microservice.
(Application is able to return both Department and User objects at the same time)

MicroserviceDCB3:
Has the @EnableEurekaServer annotation that allows application to act as a service registry.

MicroserviceDCB4:
Has the @EnableEurekaClient annotation and application.yml settings that
allow the application to act as an API Gateway.
Has the @EnableHystrix annotation and application.yml settings that
allow the application to also dictate fallback methods to be called.

MicroserviceDCB5:
Has the @EnableEurekaClient and @EnableHystrixDashboard annotations
and application.yml settings that allow the application to act as a hystrix dashboard.

MicroserviceDCB6:
Has the @EnableEurekaClient and @EnableConfigServer annotations that
allow the application to act as a configuration server.
Configuration settings are in a Github repository as defined by the application.yml.
bootstrap.yml is added to other files, dependencies (spring cloud config) is added in other files, to accommodate this.
(Check differences between B and C version for specific differences)

In order to implement Sleuth and Zipkin, zipkin section in the application.yml file of the model classes
(Department/User) were added, and appropriate dependencies were added to pom.xml file. All other applications untouched.

INSTRUCTIONS:
- "http://localhost:8761/" to access the service registry page. (Using another port seems to have issues)
- "http://localhost:9005/hystrix" to access the hystrix dashboard.
- Enter "http://localhost:9004/actuator/hystrix.stream" URL into hystrix dashboard to view microservice analytics.
- Run Zipkin on command prompt to run it. Take IP address from command prompt to get to the Zipkin UI.