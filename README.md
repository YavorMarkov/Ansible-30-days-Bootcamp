# Ansible-30-days-Bootcamp
# Day 1: Ansible Basics and Environment Setup

This is Day 1 of our 30 Days of Ansible journey. Today, we're setting up our environment and familiarizing ourselves with Ansible basics.

## Objectives:
1. Install Ansible on your local machine.
2. Understand core components of Ansible: Inventory, Modules, Playbooks, and Roles.
3. Write a simple Ansible playbook.
4. Test the playbook on a remote server or local virtual machine.

## Steps:

### Step 1: Install Ansible

Ansible is an open-source automation tool, written in Python. It's crucial to have Python installed on your machine. Once Python is ready, install Ansible by following the official [Ansible installation guide](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).

### Step 2: Understand Core Ansible Concepts

Ansible uses a simple syntax written in YAML called playbooks. YAML stands for Yet Another Markup Language. The key components you should familiarize yourself with include Inventory, Modules, Playbooks, and Roles. Go through the [official Ansible documentation](https://docs.ansible.com/ansible/latest/user_guide/index.html) to understand these concepts.

### Step 3: Write Your First Ansible Playbook

A simple Ansible playbook looks like this:

```yaml
---
- name: Install Apache
  hosts: webserver
  become: yes
  tasks:
    - name: Install httpd
      yum:
        name: httpd
        state: present
    - name: Start service httpd, if not started
      service:
        name: httpd
        state: started
```

The `hosts` value refers to the groups or hosts in your Ansible inventory on which you want to run these tasks. In the tasks, we're using the `yum` module to install Apache and the `service` module to ensure the service is started.

### Step 4: Test Your Playbook

Now, write a playbook to install a package of your choice (like git) on a remote server or a local virtual machine and execute it.

## Outcome

By the end of Day 1, you'll have a working Ansible environment on your machine, and you'll have written and executed your first Ansible playbook.

