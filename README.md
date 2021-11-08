# GCE_Instance_MySQL
Create GCE Instance CentOS7 with MySQL

# Pre-Requirements

* gcloud

[Link to the Gcloud SDK installation](https://cloud.google.com/sdk/docs/install)

* install ansible SDK

* pip install requests google-auth ansible

## When all the tools above are installed, clone this project to your local machine and run those commands in your shell:

### Change dir to the project dir
* cd GCE_Instance_MySQL

***NOTE***
To run the playbook first of all, you'll need to proceed some changes in the MySQL_Instance_GCE.yaml file:
1. Add a new key to your Service Acount on gcp as json format and download it to the project directory, 
   then add the name of this file to gcp_cred_file var, otherwise you'll not be accepted to communicate with gcp via ansible.
3. Add the project ID from gcp to gcp_project var
4. Select your region to gcp_region var, and zone to gcp_zone

# Login to GCP via gcluod SDK

* gcloud auth application-default login

# Add SSH keys to GCP

* ssh-keygen
* ./gen_ssh_to_gcp.sh

# Configure Ansible inventory

## Add this line to /etc/ansible/ansible.cfg below [inventory] block

* enable_plugins = gcp_compute

## Install GCP Collection to ansible

* ansible-galaxy collection install google.cloud

# Run the playbook

* ansible-playbook MySQL_Instance_GCE.yaml

## The CentOS7 Instance will created after the playbook finished with MySQL-server ;-)
