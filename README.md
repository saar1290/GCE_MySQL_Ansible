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
To run the playbook first of all, you'll need to proceed some changes in the MySQL_Instance_GCE.yaml and gcp_compute_plugin.gcp.yaml files:
1. Add a new key to your Service Acount on gcp as json format and download it to the project directory, 
   then add the path of this file as a GCP Credential file, otherwise you'll not be accepted to communicate with GCP via ansible.
3. Add the project ID from GCP
4. Add your region and zone

# Login to GCP via gcloud SDK

* gcloud auth application-default login

# Add SSH keys to GCP

* ssh-keygen
* ./gen_ssh_to_gcp.sh

# Configure Ansible inventory

## Add this line to /etc/ansible/ansible.cfg below [inventory] block

* enable_plugins = gcp_compute

## Install GCP Collection to ansible

* ansible-galaxy collection install google.cloud

### Enable the GCP_Compute plugin

* ansible-inventory --list -i gcp_compute_plugin.gcp.yaml

# Run the playbook

* ansible-playbook MySQL_Instance_GCE.yaml

## The CentOS7 Instance will created after the playbook finished with MySQL-server ;-)
