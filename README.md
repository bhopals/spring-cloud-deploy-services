## Introduction
- Demonstrates how to create a build and deployment pipeline.  
- How to build this pipeline and then deploy all of the services to Amazon's Elastic Container Service (ECS).

## Project Details

1.  A Spring Cloud Config server that is deployed as Docker container and can manage a services configuration information using a file system or GitHub-based repository.

2.  A Eureka server running as a Spring-Cloud based service.  This service will allow multiple service instances to register with it.  Clients that need to call a service will use Eureka to lookup the physical location of the target service.

3.  A Zuul API Gateway.  All of our microservices can be routed through the gateway and have pre, response and post policies enforced on the calls.

4.  A organization service that will manage organization data used within EagleEye.

5.  A new version of the organization service.  This service is used to demonstrate how to use the Zuul API gateway to route to different versions of a service.

6.  A special routes services that the the API gateway will call to determine whether or not it should route a user's service call to a different service then the one they were originally calling.  This service is used in conjunction with the orgservice-new service to determine whether a call to the organization service gets routed to an old version of the organization service vs. a new version of the service.

7.  A licensing service that will manage licensing data used within EagleEye.

8.  A Kafka message bus to transport messages between services.


## Software needed
1.	[Apache Maven] (http://maven.apache.org)
2.	[Docker] (http://docker.com)
3.	[Git Client] (http://git-scm.com)

## Building Docker Images

   **mvn clean package docker:build**


## Running services 

   **docker-compose -f docker/common/docker-compose.yml up**


## Build and deployment pipeline in action

- 1. GitHub will be the source repository.
- 2. Travis CI will be used to build and deploy the EagleEye microservices
- 3. Maven with Spotify’s Docker plug-in will compile code, run tests, and create the executable artifact.
- 4. The machine image will be a Docker container.
- 5. The Docker container will be committed to a Docker Hub repo.
- 6. Python will be used to write the platform tests.
- 7. The Docker image will be deployed to an Amazon Elastic Container Service (ECS).


## Related Topics
- Deployable software Artifact

- Github
- Travis CI
- Maven/Spotify Docker Plugin
- Docker
- Docker Hub
- Amazon’s EC2 Container Service (ECS)

- Build Deploy Engine
- Source Repository
- Automate Build and Deploy pipeline
- No direct human interaction to deploy a service
