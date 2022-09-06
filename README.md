#  Ubuntu Docker Vagrant Ansible

## Ubuntu Virtual Machines cluster with Docker

Customizable cluster of Ubuntu virtual machines setup with docker installed. It's very easy to increase or reduce the number of VM's simply adding or removing them from the Vagrantifile.

## Prerequisite steps

VirtualBox, Vagrant and Ansible need to be installed as prerequisites. You can find the installation steps provided in their respective official web sites.

#### VirtualBox

https://www.virtualbox.org/

#### Vagrant

https://www.vagrantup.com/


#### Ansible

https://docs.ansible.com/


## And now? How does it work


1) First you need to clone this repository

2) Next cd into the cloned git directory and be sure to see the <strong>Vagrantfile</strong> and the <strong>master_playbook</strong> files. The first one is used by Vagrant to setup the VM's, the second, instead, is used by Ansible to run commands and install software on the previously mentioned VM's.

3) Finally you need to know a few Vagrant commands to operate with the cluster using the terminal. The most important ones are:

- <strong> vagrant up --provision</strong> => spin up the cluster (--provision is used to run Ansible scripts on the VM's). In alternative you can run the <strong>start.sh</strong> in the script folder.

- <strong> vagrant status </strong> => check the status of the virtual machines. In alternative you can run the <strong>status.sh</strong> in the script folder.

- <strong> vagrant halt -f </strong> => stop all the VM's. In alternative you can run the <strong>stop.sh</strong> in the script folder.

- <strong> vagrant destroy -f </strong> => stop and destroy all the VM's. In alternative you can run the <strong>destroy.sh</strong> in the script folder.

- <strong> vagrant ssh \<vm-name\> </strong> => ssh into a VM by using its name

- <strong> vagrant --help </strong> => Vagrant help

