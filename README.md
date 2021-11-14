## Table of contents

- [General info](#general-info)
- [Tasks](#tasks)
- [How to run](#how-to-run)
- [Technologies](#technologies)
- [Risks and improvments](#risks-and-improvments)

## General info
Use Ansible to automate the process of creating an AWS EC2 instance, configuring network parameters and installing Nginx Docker containers.

## Tasks
1. The deployment should take AWS credentials and AWS region as input parameters.
2. A VPC with the required networking, don't use the default VPC.
3. Provision a “t2.micro” EC2 instance, with an OS of your choice.
4. Change the security group of the instance to ensure its security level.
5. Change the OS/Firewall settings of the started instance to further enhance its security
level.
6. Install Docker CE.
7. Deploy and start a NGINX docker container in the EC2 instance.
8. Deploy a script (or multiple scripts) on the EC2 instance to complete the following sub-
tasks:
a. Log the health status and resource usage of the NGINX container every 10 seconds
into a log file.
b. Write a REST API using any choice of programming language which is you are familiar
with and read from the above log file able to a basic search. (Provide us and
example use of your API using curl or any REST client)
9. A README.md describing what you've done as well as steps explaining how to run the
infrastructure automation and execute the script(s).
10. Describe any risks associated with your application/deployment.

## How to run
Go to the folder with ansible playbook file and run command in the terminal window:
```
ansible-playbook ansible_playbook.yml --extra-vars "aws_access_key=access aws_secret_key=secret region=ap-southeast-2"
```

## Technologies
Project is created with:

- Ansible
- AWS EC2
- Docker
- Nginx
- YAML

## Risks and improvments
- I would love to improve my solution with building a specific status-check endpoint in the backend system to verify the application is healthy.
- Simple HTTP request could be enough to check if that service container is healthy but if we need to test a few more aspects of an application’s health, we can write a custom health-check script and run it in crontab
- Docker does not stop unhealthy containers automatically and it is our job to monitor those containers, resolve any issues and restart the containers. 
- Also we can collect logs and send them to monitoring systems like Grafana, Kibana, New Relic so that we can visualise and track data in the system in real-time.

