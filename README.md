
# Ansible 30 Days Bootcamp

## Day 2: Ansible Inventory and Variables

Welcome to Day 2 of our Ansible boot camp! Today, we'll focus on Ansible inventory and variables.

### Objectives:

1. [Understand Ansible inventory and its role in managing hosts](#step-1-ansible-inventory).
2. [Learn about host patterns and how to target specific groups or individual hosts](#step-2-targeting-hosts-with-patterns).
3. [Explore different types of variables in Ansible and how to use them](#step-3-ansible-variables).


### Objectives:# Ansible 30 Days Bootcamp

## Day 2: Ansible Inventory and Variables

Welcome to Day 2 of our Ansible boot camp! Today, we'll focus on Ansible inventory and variables.

### Objectives:

1. Understand Ansible inventory and its role in managing hosts.
2. Learn about host patterns and how to target specific groups or individual hosts.
3. Explore different types of variables in Ansible and how to use them.

### Steps:

#### Step 1: Ansible Inventory

Ansible inventory is a configuration file that defines the hosts and groups of hosts that Ansible can manage. The inventory file allows you to organize your hosts into logical groups, making it easier to target specific hosts or groups in your playbooks.

Example:
Create an inventory file named `hosts.ini` and define the hosts and groups in it. You can use IP addresses or domain names to identify the hosts. For example, you can have a group named `webserver` with two hosts `web1` and `web2`, and another group named `database` with hosts `db1` and `db2`. Additionally, you can create a group named `loadbalancer` with a single host `lb`.

```ini
[webserver]
web1 ansible_host=192.168.1.10
web2 ansible_host=192.168.1.11

[database]
db1 ansible_host=192.168.1.20
db2 ansible_host=192.168.1.21

[loadbalancer]
lb ansible_host=192.168.1.30
```

Explanation: In this example, we have three groups defined: webserver, database, and loadbalancer. Each group contains hosts defined with their respective IP addresses.



#### Step 2: Targeting Hosts with Patterns

Host patterns allow you to specify which hosts or groups of hosts should be the target of your Ansible operations. You can use various patterns to select hosts based on different criteria such as group names, wildcard patterns, regular expressions, or even targeting individual hosts.

Example:
Create a playbook named `playbook.yml` and specify the desired group or host pattern in the `hosts` field. For example, you can target the `webserver` group by setting `hosts: webserver`. This means that the playbook tasks will only run on hosts belonging to the `webserver` group. In the example playbook, we have a task to install Nginx, which will be executed only on hosts within the `webserver` group.

```ini
---
- name: Example Playbook
  hosts: webserver  # Targeting the `webserver` group using the host pattern
  become: yes
  tasks:
    - name: Install nginx
      yum:
        name: nginx
        state: present
```
Explanation: In this example, the playbook targets the webserver group using the host pattern. The playbook will run the task to install Nginx only on hosts in the webserver group.


#### Step 3: Ansible Variables

Variables are a fundamental part of Ansible, enabling you to store and use values across playbooks and roles. Ansible provides different types of variables, including host variables, group variables, and extra variables.

Example:
Create a playbook named `variable_playbook.yml` and declare the variables you want to use in the `vars` section of the playbook. These variables can hold values such as numbers, strings, lists, or dictionaries. In the example playbook, we define a variable named `http_port` with the value `8080`. The playbook includes a task to display the value of the `http_port` variable using the `debug` module.

```ini
---
- name: Variable Playbook
  hosts: all
  become: yes
  vars:
    http_port: 8080  # Defining the `http_port` variable with the value `8080`
  tasks:
    - name: Display variable value
      debug:
        var: http_port

```
Explanation: In this example, the playbook defines the http_port variable with the value 8080. The debug task is used to display the value of the http_port variable.

#### Step 4: Practice with Inventory and Variables

Combining the knowledge of inventory and variables, you can create dynamic and flexible playbooks.

Example:
Create a playbook named `dynamic_variable_playbook.yml` and use variables to dynamically set values based on conditions or calculations. For example, you can use the `inventory_hostname` variable to derive another variable's value. In the example playbook, we define a variable named `app_env` using the `inventory_hostname` and the `regex_replace` filter. This variable is then used in a task to display the hostname and the environment to which the web application is being deployed.

```init
---
- name: Dynamic Variable Playbook
  hosts: all
  become: yes
  vars:
    app_env: "{{ inventory_hostname | regex_replace('^web', 'prod') }}"  # Dynamically setting the value of `app_env` variable based on `inventory_hostname`
  tasks:
    - name: Deploy web application
      command: echo "Deploying app to {{ inventory_hostname }} with env: {{ app_env }}"
```

### Outcome:

By the end of Day 2, you'll have a solid understanding of Ansible inventory, host patterns, and variables. You'll be able to target specific hosts or groups using patterns, as well as leverage variables to make your playbooks more dynamic and adaptable.

---
# Congratulations!

Congratulations on successfully completing Day 2 of the Ansible 30-day Bootcamp! Today was all about getting to grips with Ansible's inventory and variables. You've built a foundational understanding of managing hosts and deploying playbooks with targeted host patterns. This includes different types of variables and their use in Ansible to make your operations more dynamic and flexible. Well done!

As you continue this journey, remember that balance is important. Take a break, get some fresh air, socialize, and maintain your health. A healthy mind fosters better learning. Let's keep going strong for the remaining days. See you tomorrow for a new challenge! 😃

# Keep Consistency! 
Consistency is key to success in any long-term endeavor. It's better to make steady progress each day than to work intensively for a short period and burn out.

Think of this bootcamp as a marathon, not a sprint. Your goal isn't to learn everything in one day, but to make a little progress each day. Remember, nature doesn't rush, yet everything gets accomplished. Let's take this journey one day at a time and embrace the beauty of steady, consistent progress.