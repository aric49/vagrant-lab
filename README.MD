# Local Vagrant Lab

## Purpose:
Spin up a local 4 node Ubuntu 16.04 lab to test Ansible playbooks, deployments, and overall experimentation.  Will be helpful to test new configurations, run-time environments, and operations deployments.

## Intended Audience:
Anyone who wants a simple to deploy lab which can be used to spin up and tear down a four node environment quickly and painlessly. You can use Ansible as the vagrant provisioner (example included in Vagrantfile), or run Ansible core commands directly using the included inventory file. New roles and playbooks will be added in the `roles/` directory. I use this lab to experiment with new Ansible functionality before incorporating it into my production-ready playbooks. I want to share this lab with others who may wish to deploy a local lab quickly and easily.

## Getting Started:
Assuming the user already has Vagrant, Virtualbox, and Ansible installed on their local workstation, you can bring up the lab by simply navigating to the directory and executing:

`vagrant up`

This should spin up the four nodes:  `node01, node02, node03, node04`. In the vagrant provisioning, shell commands are executed which install `Python2.7`, and `python-simplejson` to ensure that Ansible will be able to be run immediately, out of the box. I understand the Vagrant shell provisioner, and the Vagrant Ansible provisioner are doing exactly the same thing. I designed it like that so the user can understand exactly how to add custom playbooks to the Ansible provisioner if they so choose.

If you choose to run playbooks using Ansible core commands, execute them like this:

`ansible-playbook Deploy_Lab.yml -i inventory.ini`

**Note: ** You may add your own roles in the `Deploy_Lab.yml` playbook.

When you are finished with the lab, simply run the vagrant destroy command as follows:

`vagrant destroy`

To see which VMs are running at any given time, execute:

`vagrant status`


## Future Plans:
Currently, this repository deploys a simple four node lab with Ubuntu 16.04 virtual machines. From there, a user may deploy any application on top of these VMs, or simply use them for any purpose. My ultimate goal is to provide sample applications which can be deployed in the `roles/` directory which may be deployed using the vagrant provisioning, or by executing the playbooks using Ansible core commands. From there, a user can experiment with changes to an application, or test various scenarios.  
