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
  hosts: webserver #your_remote_server_group_or_name
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
or the same code with explanations line by line:

```yaml
---
- name: Install Apache                                        # This playbook is for installing Apache
  hosts: webserver                                            # Specify your remote server group or name here
  become: yes                                                 # The become directive is used to gain root (or any other user's) privileges
  tasks:                                                      # The tasks directive is used to list the tasks that the playbook will execute
      - name: Install httpd                                   # The name of the first task - it's to install Apache
        yum:                                                  # The yum module is used to manage packages with the Yum package manager
          name: httpd                                         # Specify the package we want to install
          state: present                                      # We want to ensure httpd is present (installed)
      - name: Start service httpd, if not started             # The name of the second task - it's to ensure the Apache service is running
        service:                                              # The service module is used to start, stop, restart, or reload services
          name: httpd                                         # Specify the service we want to manage
          state: started                                      # We want to ensure the httpd service is started
```

The `hosts` value refers to the groups or hosts in your Ansible inventory on which you want to run these tasks. In the tasks, we're using the `yum` module to install Apache and the `service` module to ensure the service is started.

### Step 4: Test Your Playbook

Now, write a playbook to install a package of your choice (like git) on a remote server or a local virtual machine and execute it.

```yaml
---
- name: Install Git    # This is a playbook to install Git
  hosts: your_remote_server_group_or_name
  become: yes
  tasks:
    - name: Install git
      yum:
        name: git   # The package we want to install
        state: present   # We want to ensure git is present

```

## Outcome

By the end of Day 1, you'll have a working Ansible environment on your machine, and you'll have written and executed your first Ansible playbook.

# Congratulations!

You've successfully completed the first day of the Ansible 30-day Bootcamp! You've set up your environment, understood the basics of Ansible, and executed your first playbook. Well done!

As you continue this journey, remember that balance is important. Take a break, get some fresh air, socialize, and maintain your health. A healthy mind fosters better learning. Let's keep going strong for the remaining days. See you tomorrow for a new challenge! :)
can i put this too

# Keep Consistency!

Consistency is key to success in any long-term endeavor. It's better to make steady progress each day than to work intensively for a short period and burn out. 

Think of this bootcamp as a marathon, not a sprint. Your goal isn't to learn everything in one day, but to make a little progress each day. Remember, nature doesn't rush, yet everything gets accomplished. Let's take this journey one day at a time and embrace the beauty of steady, consistent progress.


