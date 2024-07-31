# labs
Local Labs enhanced by Vagrant and Ansible. Apps and tools installations from scratch to practice configuration and management.

# Vagrant misc

## Bring up the virtual machines
`vagrant up`

## Loads new config if Vagrantfile changes
`vagrant reload`

## SSH config
`vagrant ssh-config`

# Ansible misc

## Run a playbook
`ansible-playbook playbooks/bigbang.yml -i playbooks/inventory/vagrant.ini`


# Misc
List opened ports on linux:
`sudo netstat -tulpn | grep LISTEN`
