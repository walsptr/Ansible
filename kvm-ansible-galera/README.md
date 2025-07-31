# Setup galera cluster on KVM (Development Only)
this ansible will help you for easier deployment galera on kvm

## Prepare step
this step will help you for prepare the requirement for doing deployment on kvm like:
- create directory for instance, cloud init and images
- download images ubuntu-22
```
ansible-playbook -i inventory.yaml playbook.yaml --tags prepare --limit kvm
```

## Create VMs on KVM
this step will help you to create 3 VMs for galera cluster
```
ansible-playbook -i inventory.yaml playbook.yaml --tags create --limit kvm
```

## Manage VMs

Will help you to doing start and stop VMs on KVM
```
ansible-playbook -i inventory.yaml playbook.yaml --tags start --limit kvm

ansible-playbook -i inventory.yaml playbook.yaml --tags stop --limit kvm
```

## Deployment galera
this step for doing deployment galera in VMs. before doing this step make sure you can ssh the VMs
```
ansible-playbook -i inventory.yaml playbook.yaml --tags galera --limit galera
```

## Remove VMs
```
ansible-playbook -i inventory.yaml playbook.yaml --tags remove --limit kvm
```