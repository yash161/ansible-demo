# Setting Up EC2 Instances on AWS

Follow these steps to set up two EC2 instances on AWS, one as a master and the other as a slave.

## Prerequisites

Before you begin, make sure you have the following:

- An AWS account with necessary permissions.
- AWS CLI installed and configured on your local machine.

## Instructions

1. **Create EC2 Instances**
    - Log in to your AWS Management Console.
    - Navigate to the EC2 dashboard.
    - Launch two EC2 instances, naming one as "master" and the other as "slave." Ensure they have the necessary configurations and security groups.

2. **Generate SSH Keys on the Master**
    - Access the "master" instance via SSH.
    - Generate SSH private and public keys on the "master" instance using the `ssh-keygen` command.

3. **Copy Public Key to Slave**
    - On the "master" instance, copy the public key content.
    - Access the "slave" instance via SSH.
    - Open the `~/.ssh/authorized_keys` file on the "slave" instance using a text editor (e.g., `vim`).
    - Replace the existing public key content with the one you copied from the "master."

4. **SSH into Slave from Master**
    - On the "master" instance, use the `ssh` command to connect to the "slave" instance.

Now, your "master" and "slave" EC2 instances are set up and ready for use.
