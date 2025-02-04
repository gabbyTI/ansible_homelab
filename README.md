# Ansible Homelab

This repository contains Ansible playbooks and roles for automating the setup and management of my homelab environment. It is designed to streamline configuration, and maintenance of virtual machines, LXC containers, and other infrastructure components.

## Getting Started

### 1. Clone the Repository

```bash
git clone git@github.com:gabbyTI/ansible_homelab.git
cd ansible_homelab
```

### 2. Set Up Your Inventory

Edit the `inventory/hosts.yml` file and define your hosts:

```yml
all:
  children:
    demos:
      hosts:
        demo1:
          ansible_host: 192.168.2.76
        demo2:
          ansible_host: 192.168.2.25
    homelab:
      hosts:
        localhost:
          ansible_connection: local
```

### 3. Run a Basic Connectivity Test

```bash
ansible -i inventory/hosts.yml all -m ping
```

### 4. Apply a Playbook

To update all packages on your homelab servers:

```bash
ansible-playbook -i inventory playbooks/update_system.yml
```

## Repository Structure

```
ansible_homelab/
├── inventory             # Inventory folder for host seperation (eg: staging/ and production)
│   ├── hosts.yml         # Inventory file listing managed hosts
├── playbooks/            # Ansible playbooks for automation
│   ├── bootstrap_lxc.yml # Setup SSH and ansible user in LXC
│   ├── update_system.yml # Automate system updates
├── roles/                # Ansible roles for modular automation
│   ├── common/           # Common tasks
├── group_vars/           # Variables per group of hosts
├── host_vars/            # Variables per individual host
├── .gitignore            # Ignore sensitive files and unnecessary logs
├── README.md             # Documentation
├── requirements.yml      # ansible galaxy requirements
├── ansible.cfg           # Setting Default values
```
---

📌 **Author:** Gabriel Ibenye  
🔗 **GitHub:** [gabbyTI](https://github.com/gabbyTI) 
