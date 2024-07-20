# Ansible Docker CV Deployment

This project automates the deployment of a CV (Curriculum Vitae) web page using Ansible and Docker. The setup involves running an Nginx server inside a Docker container, which serves the CV HTML file.

## Prerequisites

Before you begin, ensure you have the following installed:

1. **Ansible** on your control machine (the machine from which you will run the playbook).
2. **Docker** on the target machine (the machine on which the Docker container will be deployed).

## Project Structure

- `Dockerfile`: Defines the Docker image.
- `index.html`: Your CV HTML file.
- `deploy.yml`: Ansible playbook to deploy the Docker container.
- `hosts`: Ansible inventory file.

## Step-by-Step Deployment Guide

### 1. Clone the Repository

First, clone this repository to your local machine:

```sh
git clone https://github.com/yourusername/ansible-docker-cv-deployment.git
cd ansible-docker-cv-deployment
```

### 2. Update the hosts File

Open the hosts file and update it with your target machine's details. Replace 103.151.111.241 and root with your actual IP address and username.

```ini
[debian_agents]
opsoura3 ansible_host=103.151.111.241 ansible_user=root
```

### 3. Place Your index.html File

Ensure that your index.html file (your CV) is placed in the repository root directory.

### 4. Run the Ansible Playbook

Execute the following command to run the Ansible playbook, which will handle the deployment:

```sh
ansible-playbook -i hosts deploy.yml
```

This command will perform the following tasks:

   1. Install Docker on the target machine.
   2. Start the Docker service.
   3. Create a project directory on the target machine.
   4. Copy the Dockerfile and index.html to the target machine.
   5. Build the Docker image.
   6. Run a Docker container with the built image, exposing it on port 80.

## Troubleshooting

If you encounter any issues, here are some common troubleshooting steps:

   - **Check Ansible Version**: Ensure you are using a compatible version of Ansible.
   - **SSH Connection**: Verify that your control machine can SSH into the target machine without password prompts.
   - **Docker Installation**: Ensure Docker is installed correctly on the target machine.

