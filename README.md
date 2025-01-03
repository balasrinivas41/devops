i# Create S3 bucket
Full Workflow Example:
Create a bucket in Mumbai (ap-south-1):

# AWS S3 CLI Operations

This document provides instructions for using the AWS CLI to interact with Amazon S3 buckets, including listing files, viewing their contents, and deleting objects.

## Prerequisites

- **AWS CLI** installed and configured with your AWS credentials. If you haven't configured the CLI, run the following command:
  
  ```bash
  aws configure

  ##create s3 bucket
  aws s3api create-bucket --bucket bala --region ap-south-1 --create-bucket-configuration LocationConstraint=ap-south-1

  ##list buckets  
  aws s3api list-buckets --region ap-south-1

  ##create file in bucket
  aws s3 cp bala.js s3://bala/
  
  ## remove files from s3 bucket  
  aws s3 rm s3://bala --recursive
  
  ##delete s3 bucket
  aws s3api delete-bucket --bucket bala --region ap-south-1

### create ec2 instance
  ```bash
  ## create default ec2 instance which are ansible server to configure target server
  aws ec2 run-instances \
    --image-id ami-0e2c8caa4b6378d8c \
    --instance-type t2.micro \
    --key-name docker \
    --security-groups default \
    --count 2 \
    --region us-east-1
 ```bash
 ## Install ansible in ansible server
 
 sudo apt install ansible
 ansible --version
 ## Generate ed25519 keys in two ec2 instances
 
 ssh-keygen
 ## It generates public key and private key, copy public key to authorized_keys file /home/ubuntu/.ssh/id_ed25519.pub
 
 ~/.ssh/authorized_keys
 ## Create file anaconda in target instance

 ansible -i nodes all -m "shell" -a "touch anaconda" 
 

### Ansible playbook to install and start ngnix

---
- name: Install and Start Nginx
  hosts: all
  become: yes  # Run tasks with sudo/root privileges
  tasks:
    - name: Ensure Nginx is installed
      apt:
        name: nginx
        state: present
        update_cache: yes

    - name: Start and enable Nginx service
      service:
        name: nginx
        state: started
        enabled: yes

    - name: Ensure Nginx is running
      shell: systemctl status nginx
      register: nginx_status
    - name: Printing the nginx status
      debug:
        var: nginx_status.stdout_lines
...

