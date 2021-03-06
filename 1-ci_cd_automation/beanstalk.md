# Elastic Beanstalk

## What's Elastic Beanstalk

* With Elastic Beanstalk it's possible to deploy, monitor and scale an application quickly.
* It has a highly abstract focus towards infrastructure, focusing on components and performance.

## Components

### Applications

* Applications are the high level structure in Elastic Beanstalk
* Either the entire application is one EB application or each logical component of you application can be a EB application or a EB environment within an application.

### Application Versions

* Unique packages which represent versions of apps
* An application is uploaded as an application bundle (zip file)

### Environments

* Environments represents a isolated self-contained set of components and infrastructure.
* Applications can have multiple environments.
* Environments are either single-instance or scalable.
* It can be a Web Server environment or Worker environment 
* URLs for Web Server environments can be swapped between environments, which allows Blue/Green deployment.
* List of supported environments:
    * NodeJS
    * PHP
    * Go
    * Java
    * Python
    * Ruby
    * Tomcat
    * Microsoft IIS
    * Docker
        * Generic Docker containers
        * Glassfish
        * Go
        * Python

## ebextensions

* It's a configuration folder within EB application bundle
* ebextensions allows granular configuration of the environment and customization of its resources (EC2, ELB and others)
* All the files within .ebextension folder are YAML formatted and end with a .config extension. These files contain a number of key sections:
    * `option_settings`: allows declaration of global configuration options
    * `resources`: allows to specify additional resources to provision in the environment
    * `packages`, `sources`, `files`, `users`, `groups`, `commands`, `container_commands` and `service` allow customization of the EC2 instances as part of your environment.


## Docker 

* Supported Docker platforms:
    * Python
    * Ruby
    * PHP
    * NodeJS
    * Go
* For unsupported platform, it's necessary to build a Docker container with desired configurations or use a image from a registry.
* To deploy a container from an existing registry, the `Dockerrun.aws.json` file needs to be configured. This file defines the registry configuration, the port to be exposed and mappings.
* When using a private registry, the `.dockercfg` file needs to be present and configured. It contains all the authentication information. It's stored on S3 in a bucket in the same region as Elastic Beanstalk env.


