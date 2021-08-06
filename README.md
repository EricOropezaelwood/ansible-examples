# Ansible  


![alt text](https://geekflare.com/wp-content/uploads/2019/06/ansible-beginner-1200x385.jpg)  


### What it do  
Makes stuff like ```apt install tree``` easy to manage and run automatically  
via .yml files.  

### Directory Structure  
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

### Run a playbook  
Install terraform on host machine  
```ansible-playbook playbooks/terraform/main.yml```  

### AWS  
To run on AWS on an EC2 we need a hosts file and to place the public ip of the  
instance in there. Also, be able to connect via ssh.  
```ansible-playbook -i hosts playbooks/terraform/main.yml -u <USER> --private-key=~/.ssh/<YOUR-KEY>```