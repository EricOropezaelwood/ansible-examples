# Ansible  

![alt text](https://geekflare.com/wp-content/uploads/2019/06/ansible-beginner-1200x385.jpg)  

## Table of Contents
* [What it do](#What-it-do)
* [Directory Structure](#Directory-Structure)
* [Configuration](#Configuration)
* [Call Roles in a Playbook](#Call-Roles-in-a-Playbook)
* [Run a playbook](#Run-a-playbook)
* [AWS](#AWS)
* [Errors](#Errors)

## What it do  
Makes stuff like ```apt install tree``` easy to manage and run automatically  
via .yml files.  

## Directory Structure  
**disclaimer:**  
based on preference, subject to change  


```
project
│   README.md
│
└───playbooks
│   └───personal-dev-environment
│   |   │   main.yml
│   └───jenkins
|       |   main.yml
│       │   ...
│   
└───roles
|   └───terraform
|   │   └───tasks
|   │   |   └───main.yml
|   │   └───vars
|   │       └───main.yml
|   └───command-line-tools
|   │   └───tasks
|   │   |   └───main.yml
|   │   └───vars
|   │       └───main.yml
└───hosts
```

## Configuration  
```ansible.cfg``` lets us set where roles are called and our inventory location  
In ansible.cfg add the following to set roles and where to grab hosts  
```
[defaults]
inventory       = ansible/hosts
roles_path      = ansible/roles
```

## Call Roles in a Playbook  
With the roles path configured, we can call them from a playbook.yml like so:  
```
  ...
  roles:
    - terraform
  ...
```

## Run a playbook  
Install terraform on host machine  
```ansible-playbook playbooks/terraform/main.yml```  

## AWS  
To run on AWS on an EC2 we need a hosts file and to place the public ip of the  
instance in there. Also, be able to connect via ssh.  
```ansible-playbook -i hosts playbooks/terraform/main.yml -u <USER> --private-key=~/.ssh/<YOUR-KEY>```

## Errors  
For running on localhost, if you see an error about sudo being required then run  
```sudo apt update``` on your machine to enable sudo for the moment. There must  
be a better solution...

