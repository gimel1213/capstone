# Udacity Capstone DevOps Nanodegree

## Introduction

This is the capstone project for udacity devops ingineer. Pipeline details are as follows.

## Technologies

* [Bcrypt Sandbox](https://github.com/felladrin/bcrypt-sandbox), as the main application.
* Docker, for building a ready-deploy application.
* Kubernetes(AWS EKS), for automating deployment, scaling, and management of containerized applications.
* CloudFormation, for agentless IT automation.
* Aqua Microscanner, for docker protection, monitoring, logging and real-time analysis.
* Jenkins, for automatic integrations and deployments(CI/CD).

## How to Setup Infrastructure
  - To setup the cloudformation stacks  the makefile in the Infra folder ,run "make deploy" with your aws profile setupped


## Setup Jenkins with plugins and nessassary packages
  - configure the jenkins server with the pluggins Aqua Microscanner and pipeline aws
  - setup awscli new version, userpermissions to eks,kubectl etc for jenkins
  - blues ocean ui has been used
  - setup the credentails for docker and aws in jenkins credentails


## Rolling update
  - initaially the deployment with the initial UI.And then change some text  in the UI and do a rolling update which will trigger after merging the code to the master branch.
  - rolling update will be managed by kubernetes deployment type.after the new pods are up and running the old pods will be deleted automatically.
  - that'll do it.
