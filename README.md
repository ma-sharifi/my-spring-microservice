## Customized-Spring Microservices in Action - Second Edition. Chapter 12
This is a customized version of this [project] (https://github.com/ma-sharifi/manning-spring-mcroservice)

## The purpose of this project
1. Update the project to the newest features like Jib
2. Add more microservice design pattern like CQRS
3. Add different test
4. and more

## How to Clone project
We change the project to multiple submodules to work on the module in a team.
```bash
# Clone this repository
$ git clone https://github.com/ma-sharifi/my-spring-microservice.git
````
## How to fetch submodules
```shell
git submodule update --init --recursive
git submodule foreach git pull origin main 
```
##Build docker image
We used JIB, in parent just run the following command:

```shell
mvn compile jib:build
```

# Introduction
Welcome to Spring Microservices in Action, Chapter 12.  Chapter 12 is almost the end of the book and demonstrates how to create a build and deployment pipeline.  We walkthrough how to build this pipeline and then deploy all of the services to Amazon's Elastic Kubernetes Service (EKS). 

By the time you are done reading this chapter you will be able to build and/or deploy:

1. A Spring Cloud based OAuth2 authentication service that can issue and validate JWT tokens.  
2. A Spring Cloud Config server that is deployed as Docker container and can manage a services configuration information using a file system or GitHub-based repository.
3. A Eureka server running as a Spring-Cloud based service. This service will allow multiple service instances to register with it. Clients that need to call a service will use Eureka to lookup the physical location of the target service.
4. A API Gateway. All of our microservices can be routed through the gateway and have pre, response and post policies enforced on the calls.
5. A organization service that will manage organization data used within Ostock.
6. A licensing service that will manage licensing data used within Ostock.
7. A Postgres SQL database used to hold the data.
8. A Kafka message bus to transport messages between services.
9. A Redis service to act as a distributed cache.
9. A set of ELK Stack applications (Elasticsearch, Logstash, Kibana)
10.A Zipkin Server

Our PostgreSQL database and Redis service have now been moved to Amazon services.

You can find all of the service.yaml and deployment.yaml files in the AWS folder. Also all the required configuration to create the ELK stack EC2 instance.


# The build command

Will execute the [Spotify dockerfile plugin](https://github.com/spotify/dockerfile-maven) defined in the pom.xml file.  

 Running the above command at the root of the project directory will build all of the projects.  If everything builds successfully you should see a message indicating that the build was successful.

# The Run command

This command will run our services using the docker-compose.yml file located in the /docker directory. 

If everything starts correctly you should see a bunch of Spring Boot information fly by on standard out.  At this point all of the services needed for the chapter code examples will be running.

# Database
You can find the database script as well in the docker directory.

### Contributing
Feel free to help us to add a lot of microservice pattern to this project.