![image](https://github.com/user-attachments/assets/7d932f7f-d698-4e6d-81eb-8a1bed572d92)


## 📂 Document Info

| Author   | Created on | Version  | Last Edited On | Internal-Reviewer | L0-Reviewer  | L1-Reviewer | L2-Reviewer  |
|----------|------------|----------|----------------|-------------------|--------------|-------------|--------------|
| kanika  | 18-04-25   | version 2| 19-04-25       | priyanshu     | priyanka Balidkar| Rishabh sharma | Piyush upadyay |


# 📘 Ansible Static Inventory Documentation



## 📑 Table of Contents

- [Where to Place Inventory Files](#where-to-place-inventory-files)
- [Overview](#overview)
- [🛠️ Key Steps to Follow](#keysteps-to-follow)
  - [1. Create the Inventory File](#1-create-the-inventory-file)
  - [2. Understanding the Structure](#2-understanding-the-structure)
    - [Groups](#groups)
    - [Server Entries](#server-entries)
    - [Group Variables](#group-variables)
    - [Parent Group](#parent-group)
  - [3. Special Settings for Ansible](#3-special-settings-for-ansible)
    - [ansible_user](#ansible_user)
    - [ansible_ssh_private_key_file](#ansible_ssh_private_key_file)
    - [ansible_ssh_common_args](#ansible_ssh_common_args)
  - [4. Run Ansible Commands](#4-run-ansible-commands)
- [⚙️ ansible.cfg Configuration](#️-ansiblecfg-configuration)
- [Contact Information](#contact-information)
- [Documentation Reference](#documentation-reference)


#  Where to Place Inventory Files

- **Default**: `/etc/ansible/hosts` 🗂️

- **Custom Path**: You can specify a custom path using the `-i` option with Ansible commands:
  ```bash
  ansible -i <path> <command> ⚙️
   ```

#  Overview

An Ansible Inventory is a file that defines the list of hosts (servers or devices) that Ansible can manage. In a static inventory, the list is manually defined and does not change unless edited by a user. It contrasts with dynamic inventories that pull host data from external sources like cloud providers 🌐.

# keysteps to follow

## 1. Create the Inventory File
Ansible uses an inventory file to define the servers you want to manage. This file can be in INI format, YAML, or JSON. For simplicity, we'll use INI format in this example.


```ini
## Static inventory example

# Grouping servers
[web_servers]
web1.example.com ansible_user=ubuntu
web2.example.com ansible_user=ubuntu

[db_servers]
db1.example.com ansible_user=centos
db2.example.com ansible_user=centos

# Defining a group with IP addresses
[api_servers]
10.0.0.1 ansible_user=admin
10.0.0.2 ansible_user=admin

# If needed, group all servers under a default group
[all_servers:children]
web_servers
db_servers
api_servers

# Variables specific to a group
[web_servers:vars]
http_port=80
max_clients=200

[db_servers:vars]
db_port=3306
db_user=admin

[api_servers:vars]
api_port=8080
```

## 2. Understanding the Structure

### Groups
- The `[web_servers]`, `[db_servers]`, and `[api_servers]` sections are groups. Servers are grouped for better organization, making it easier to manage tasks and configurations specific to each role.

### Server Entries
- Each server is listed by its hostname (e.g., `web1.example.com`) or IP address (e.g., `10.0.0.1`), followed by any group-specific variables. For example, `ansible_user` defines the SSH username used to connect to the server.

### Group Variables
- Group-specific variables are defined under each group. These variables can configure settings particular to each server group, such as `http_port` for web servers or `db_port` for database servers.

### Parent Group
- The `[all_servers:children]` group combines other groups (e.g., `web_servers`, `db_servers`, `api_servers`) under one umbrella. This is useful for applying global commands or tasks across all servers in the inventory.

## 3. Special Settings for Ansible

To ensure your Ansible commands work correctly, you may need to include additional parameters like:

### ansible_user
- Specifies the SSH user to log in with. This is necessary for Ansible to connect to the servers with the correct user account.

### ansible_ssh_private_key_file
- *(Optional)* If you are using SSH keys for authentication, specify the path to the private key file to use for SSH connections.

### ansible_ssh_common_args
- *(Optional)* If you need to set specific SSH options (such as disabling strict host checking), you can define them using this parameter.


## 4. Run Ansible Commands

Once your static inventory is set up, you can run Ansible commands targeting the groups you’ve defined.

For example:

### Running a playbook targeting web servers

```bash
# Running a playbook targeting web servers
ansible-playbook -i inventory.ini site.yml -l web_servers

# Running an ad-hoc command to check connectivity to all servers
ansible all -i inventory.ini -m ping

# Running an ad-hoc command to check connectivity to db servers
ansible db_servers -i inventory.ini -m ping
```

# ⚙️ ansible.cfg Configuration

If you want Ansible to use a specific inventory file by default, configure `ansible.cfg`:

```ini
[defaults]
inventory = ./inventory/inventory.ini
remote_user = ubuntu
host_key_checking = False
```


#  Contact Information


| Name       | Email Address                |
|------------|------------------------------|
| Pravalika  | kanikarapu.pravalika.snaatak@mygurukulam.co|

##  Documentation Reference

| **Link** | **Description** |
|----------|-----------------|
| [Ansible Inventory Guide](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html) | Official documentation followed for setting up and organizing static inventories in Ansible. |




