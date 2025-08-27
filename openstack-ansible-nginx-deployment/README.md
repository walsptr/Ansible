# OpenStack Ansible Nginx Deployment

This is a simple IAC on openstack for deploying instance on openstack and install nginx in instance

1. you need to edit the clouds.yaml, make sure it's fit with your auth for openstack.
2. edit the deploy_vm.yaml, edit in this var:
```
    instance_name: nginx-vm
    image_name: Ubuntu-22
    flavor_name: m1.nano
    network_name: testing
    keypair_name: test
    security_groups:
      - default
    floating_network: ext_net
```
make sure your security group enable ssh and http ingress for checking the nginx
3. don't forget to install ansible and openstacksdk, install galaxy collection and export the ansible config
```
cd openstack-ansible/
python3 -m venv .venv
source .venv/bin/activate
pip install ansible openstacksdk
ansible-galaxy collection install openstack.cloud
export ANSIBLE_CONFIG=~/openstack-ansible/ansible.cfg
```
4. running this command for testing
```
ansible-playbook deploy_vm.yaml
```