# labs
Local Labs enhanced by Vagrant and Ansible. Apps and tools installations from scratch to practice configuration and management.

# VMs shared folder

Shared folders can be used to make simple Data Pipelines where Data Storage is not the learning subject.

## Creating folder on Host
```
sudo mkdir /var/vms_shared_folder/
sudo chown -R $USER /var/vms_shared_folder/
```

## Folder on Guest
```
ls /var/labs/
```


# Vagrant misc

## Bring up the virtual machines
`vagrant up`

## Loads new config if Vagrantfile changes
`vagrant reload`

## SSH config
`vagrant ssh-config`

After start the VM, it is necessary configure SSH to use the insecure shared key on ` ~/.ssh/config`.

For single machine use the name of the host, for clusters use host name with wildcard:

**Single VM sample:**

```
Host airflow-simple
  Hostname 127.0.0.1
  User vagrant
  UserKnownHostsFile /dev/null
  StrictHostKeyChecking no
  PasswordAuthentication no
  IdentityFile ~/.vagrant.d/insecure_private_key
  IdentitiesOnly yes
  LogLevel FATAL
```

**Cluster VM sample:**
```
Host kafka*
  Hostname 127.0.0.1
  User vagrant
  UserKnownHostsFile /dev/null
  StrictHostKeyChecking no
  PasswordAuthentication no
  IdentityFile ~/.vagrant.d/insecure_private_key
  IdentitiesOnly yes
  LogLevel FATAL
```

# Routing to VMs:

The `nat_router` has a non-internal Host-Only network interface, to route communication to `nat_router`, create routes bellow on host machine:

```
sudo ip route add 192.168.60.0/24 via 192.168.56.4
sudo ip route add 192.168.61.0/24 via 192.168.56.4
sudo ip route add 192.168.62.0/24 via 192.168.56.4
```

# Ansible misc

## Run a playbook
`ansible-playbook playbooks/bigbang.yml -i playbooks/inventory/vagrant.ini`


# Misc
List opened ports on linux:
`sudo netstat -tulpn | grep LISTEN`
