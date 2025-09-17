# 🚀 Talos Linux Multi-Master Deployment on OpenStack (RHOSP) with Ansible

Ansible playbooks & roles to provision a **Talos Linux** Kubernetes cluster (multi-master, with load balancer) on **Red Hat OpenStack Platform (RHOSP)**.  
This automation follows best-practice Ansible structure (roles, group_vars, inventories).

---

## 📂 Repository Structure

```
├── ansible.cfg
├── collections
│   └── requirements.yml
├── inventories
│   ├── group_vars
│   │   └── all.yml
│   └── hosts.yml
├── playbooks
│   ├── artifacts
│   ├── destroy.yml
│   └── prov.yml
├── README.md
├── roles
│   ├── openstack_fips
│   │   └── tasks
│   │       └── main.yml
│   ├── openstack_images
│   │   └── tasks
│   │       └── main.yml
│   ├── openstack_keypair
│   │   └── tasks
│   │       └── main.yml
│   ├── openstack_lb_members
│   │   └── tasks
│   │       └── main.yml
│   ├── openstack_loadbalancer
│   │   └── tasks
│   │       └── main.yml
│   ├── openstack_networking
│   │   └── tasks
│   │       └── main.yml
│   ├── openstack_ports
│   │   └── tasks
│   │       └── main.yml
│   ├── openstack_security
│   │   └── tasks
│   │       └── main.yml
│   ├── openstack_servers_controlplane
│   │   └── tasks
│   │       └── main.yml
│   ├── openstack_servers_jump
│   │   └── tasks
│   │       └── main.yml
│   ├── openstack_servers_workers
│   │   └── tasks
│   │       └── main.yml
│   ├── talos_bootstrap
│   │   └── tasks
│   │       └── main.yml
│   ├── talos_check
│   │   └── tasks
│   │       └── main.yml
│   ├── talos_config
│   │   └── tasks
│   │       └── main.yml
│   ├── talos_ingress
│   │   └── tasks
│   │       └── main.yml
│   ├── talos_kubeconfig
│   │   └── tasks
│   │       └── main.yml
│   └── talos_occm
│       └── tasks
│           └── main.yml
└── templates
    ├── cloud.conf
    └── patch.yaml
```

# Preparation
- Set up cloud.conf in templates directory
- To get application credential id & secret, run this command
```
openstack application credential create <name>
```
- if you want custom more on talos linux use patch.yaml in templates directory

# How to running
```
ansible-playbook -i inventories/hosts.yml playbooks/prov.yml
```

# How to destroy
```
ansible-playbook -i inventories/hosts.yml playbooks/destroy.yml
```