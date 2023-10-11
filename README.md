# Youcan Devops task - Coding challenge III: Save our app from DDos attacks.

In this DevOps task, I demonstrated the use of HAProxy's in-memory stick table to secure our platform by tracking our users` activities, including malicious ones.

## __Step 1: Setting Up the Environment__

__Provisioning VMs__

Provision two Ubuntu VMs:

__deploy:__ This VM serves as the deployment environment for the remote server.
__remote:__ This VM is configured to act as the remote server.

__SSH into the Deployment VM__

Log in to the __deploy__ VM using SSH.

__Installing Dependencies__

Use the provided __ansible-docker.sh__ script to install the required packages on the __deploy__ VM, including __ansible__, __docker__ and __docker compose__.

`chmod +x ansible-docker.sh`

`./ansible-docker.sh`

## __Step 2: Directory Structure Setup__

Create the necessary directory structure on the deploy VM:

- __php:__ This directory will hold the __index.php__ file.
- __ansible:__ This directory is designated for Ansible __roles__ and the __ansible.cfg__ configuration file.
- __nginx:__ Store the __default.conf__ file here.
- __haproxy:__ This directory will contain the __haproxy.cfg__ file.

__Ansible Configuration for Remote VM__

We will use Ansible to configure the remote VM. Ensure that you have added the private key of the remote VM to the deploy VM for seamless SSH access.

eval `ssh-agent -s`

`ssh-add <remote-private-key>`

Next, execute the Ansible playbook using the following command:

`ansible-playbook -i inventory.yml playbook.yml`

__Accessing the Application__

To access the PHP sample website hosted on the __remote__ VM, use its Public IP address or DNS:

`http://<remote-public-IP-or-DNS>`

Access the __HAProxy statistics report__ at:

`http://<remote-public-IP-or-DNS>/haproxy?stats`

__username:__ admin

__password:__ admin

To view logs for the __Nginx__ and __HAProxy__ containers, use the following commands:

`docker logs <nginx-container-id>`

`docker logs <haproxy-container-id>`

__N/B:__ 
I used an empty file to represent the __remote-private-key__.



