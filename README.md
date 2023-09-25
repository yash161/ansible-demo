# Setting Up EC2 Instances and Ansible

This guide provides step-by-step instructions on setting up two EC2 instances on AWS, designating one as a master and the other as a slave, and installing Ansible for efficient configuration management.

## Prerequisites

Before you begin, ensure you have the following prerequisites:

- An AWS account with appropriate permissions.
- AWS Command Line Interface (CLI) installed and configured on your local machine.

## Instructions

1. **Create EC2 Instances**
    - Log in to your AWS Management Console.
    - Navigate to the EC2 dashboard.
    - Launch two EC2 instances, naming one as "master" and the other as "slave." Configure their settings, including security groups, as required.

2. **Install Ansible on Master Node**
    - Access the "master" instance via SSH.
    - Update the package list using the following command:
        ```
        sudo apt update
        ```
    - Add the Ansible PPA and update it with the following commands:
        ```
        sudo add-apt-repository --yes --update ppa:ansible/ansible
        ```
    - Install Ansible with this command:
        ```
        sudo apt install ansible
        ```

3. **Generate SSH Keys on Master**
    - On the "master" instance, generate SSH private and public keys using the `ssh-keygen` command.

4. **Copy Public Key to Slave**
    - On the "master" instance, copy the content of the public key.
    - Access the "slave" instance via SSH.
    - Open the `~/.ssh/authorized_keys` file on the "slave" instance using a text editor (e.g., `vim`).
    - Replace the existing public key content with the one copied from the "master."

5. **SSH into Slave from Master**
    - On the "master" instance, use the `ssh` command to connect to the "slave" instance.

6. **Creating Files from Master**
    - To create a file on all hosts:
        ```
        ansible -i inventory all -m "shell" -a "touch yashtest"
        ```
    - To execute the command on a specific host group (e.g., "dbserver" in this case):
        ```
        ansible -i inventory dbserver -m "shell" -a "touch yashtestdb"
        ```

## Inventory File

Before using Ansible, you should create an "inventory" file. This file defines your hosts and host groups. Here's an example of an inventory file:
```
[webserver]
172.31.85.179

[dbserver]
172.31.94.101
```

Now, you've successfully set up two EC2 instances, installed Ansible on the "master," and configured SSH access between them. You can leverage Ansible for efficient configuration management and easily establish SSH connections between the instances.
