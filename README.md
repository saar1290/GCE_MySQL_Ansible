# GCE_MySQL_Ansible
Create GCE Instance CentOS7 with MySQL

# Pre-Requirements

* gcloud

[Link to the Gcloud SDK installation](https://cloud.google.com/sdk/docs/install)

* install ansible SDK

* pip install requests google-auth ansible

## When all the tools above are installed, clone this project to your local machine and run those commands in your shell:

### Change dir to the project dir
* cd GCE_MySQL_Ansible

***NOTE***

To run the playbook first of all, you'll need to do some changes in those files:

* Deploy_GCE_MySQL.yaml 
* gcp_compute_plugin.gcp.yaml

1. Add a new key to your "Compute Engine default service account" on gcp as json format and download it to the project directory, 
   then add the path of this file insted of "PATH_TO_CREDENTIAL_FILE", otherwise you'll not be accepted to communicate with GCP via ansible.
3. Add your project ID from GCP
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

* ansible-playbook Deploy_GCE_MySQL.yaml

## The CentOS7 Instance will created after the playbook finished with MySQL-server ;-)
