# Setting Up EC2 Instances and Ansible

Follow these steps to set up two EC2 instances on AWS, one as a master and the other as a slave, and install Ansible for configuration management.

## Prerequisites

Before you begin, make sure you have the following:

- An AWS account with necessary permissions.
- AWS CLI installed and configured on your local machine.

## Instructions

1. **Create EC2 Instances**
    - Log in to your AWS Management Console.
    - Navigate to the EC2 dashboard.
    - Launch two EC2 instances, naming one as "master" and the other as "slave." Configure them as needed, including security groups.

2. **Install Ansible on Master Node**
    - Access the "master" instance via SSH.
    - Update the package list: `sudo apt update`
    - Add the Ansible PPA and update: `sudo add-apt-repository --yes --update ppa:ansible/ansible`
    - Install Ansible: `sudo apt install ansible`

3. **Generate SSH Keys on Master**
    - On the "master" instance, generate SSH private and public keys using the `ssh-keygen` command.

4. **Copy Public Key to Slave**
    - On the "master" instance, copy the public key content.
    - Access the "slave" instance via SSH.
    - Open the `~/.ssh/authorized_keys` file on the "slave" instance using a text editor (e.g., `vim`).
    - Replace the existing public key content with the one you copied from the "master."

5. **SSH into Slave from Master**
    - On the "master" instance, use the `ssh` command to connect to the "slave" instance.

Now, you have set up two EC2 instances, installed Ansible on the "master," and configured SSH access between them. You can use Ansible for configuration management and easily SSH between the instances.
