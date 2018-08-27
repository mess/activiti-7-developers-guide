# Activiti Cloud Quickstart Guide

[![Activiti](/assets/Acitiviti_Icon_FullColor_GitHub_400x400.png)](https://github.com/Activiti)

Welcome to the new Activiti Cloud project. This Quickstart is aimed to let you get up and running with Activiti Cloud BPM in almost no time.

Due to its ultra scalable and modular design, there are several components to download and start. We want to hide this complexity until you are ready for deployment. For testing and proof of concept purposes, this quickstart is more than enough to encourage you to try your own BPMN processes inside Activiti.  
For this Quickstart guide to work, you need to have [Docker](http;//www.docker.com) and [Git](http://git.com) installed in your machine. If not, please begin by downloading and setting it up in your environment.

_We recommend to check out the 'develop' branch which is the one that we are currently updating._

Once you have Docker up and running, follow the next steps

* `git clone https://github.com/Activiti/activiti-cloud-examples`  
* \(Optional\) `git checkout develop`
* `cd activiti-cloud-examples`  
* `echo '127.0.0.1 activiti-cloud-sso-idm' | sudo tee -a /etc/hosts`  
* `cd docker`  
* `docker-compose -f infrastructure-docker-compose.yml up -d`  
* `docker-compose -f application-docker-compose.yml up -d`

Now your services will be exposed through the Gateway component at [http://localhost:8080/](http://localhost:8080/)

You can use the [Postman](https://www.getpostman.com) Collection to interact with the services that you can find here:  
[https://github.com/Activiti/activiti-cloud-examples/blob/master/Activiti v7 REST API.postman\_collection.json](https://github.com/Activiti/activiti-cloud-examples/blob/master/Activiti v7 REST API.postman_collection.json)

After importing this collection to [Postman](https://www.getpostman.com) you need to setup your environment  
you need to create an enviroment with the following values:

* gateway: [http://localhost:8080](http://localhost:8080)
* idm: [http://activiti-cloud-sso-idm:8180](http://activiti-cloud-sso-idm:8180)
* realm: springboot

![](/assets/postman-environment.png)

A basic use case: 

 * Getting a token from one of the **keycloak** folder endpoints: *getKeycloakToken <user_type>*
 * Starting a process using *startProcess* or *startProcessWithVariables* endpoints in **rb-my-app** folder
 * Checking in **query** which instances are running through *queryProcessInstances*
 * Checking events in **audit** by means of *getEvents*

If routes are to be checked, it is required to change the endpoint *routes* in **gateways** folder to:
> {{gateway}}/actuator/routes

To shut everything down run:

> docker-compose -f application-docker-compose.yml down
>
> docker-compose -f infrastructure-docker.yml down

## Next Steps

Despite the complexity of the previous steps you now have the possibility to write infinitely scalable processes, up to global scale  
This is the power of Activiti 7 and Activiti Cloud!

For more extensive and comprehensive documentation please refer to the [Getting Started Guide](./getting-started/getting-started.md)

