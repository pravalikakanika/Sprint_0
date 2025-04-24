![image](https://github.com/user-attachments/assets/7d932f7f-d698-4e6d-81eb-8a1bed572d92)


| Date       | Version | Description              | Changed By             | Pre-Reviewer        | L0               | L1              | L2               |
|------------|---------|--------------------------|-------------------------|---------------------|------------------|------------------|------------------|
| April 18   | v1.0    | Initial Draft            | Pravalika Kanikarapu   | Priyanshu                   | Khushi Malhothra | Rishabh Sharma   | Piyush Upadhyay  |
| April 19   | v1.1    | Updated documentation.md | Pravalika Kanikarapu   | Priyanshu                 | Khushi Malhothra | Rishabh Sharma   | Piyush Upadhyay  |
| April 20   | v1.2    | Updated documentation.md | Pravalika Kanikarapu   | Priyanshu                   | Khushi Malhothra | Rishabh Sharma   | Piyush Upadhyay  |
| April 24   | v1.3    | Updated documentation.md | Pravalika Kanikarapu   | Priyanshu                   | Khushi Malhothra | Rishabh Sharma   | Piyush Upadhyay  |


#  Ansible Static Inventory Documentation



##  Table of Contents
- [Introduction](#Introduction)
- [What is static Inventory](#what-is-static-inventory)
- [Why static Inventory](#why-static-inventory)
- [Where to Place Inventory Files](#where-to-place-inventory-files)
- [Overview](#overview)
- [ Key Steps to Follow](#keysteps-to-follow)
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
- [ansible Configuration](#ansible-configuration)
- [Conclusion](#conclusion)
- [Contact Information](#contact-information)
- [Documentation Reference](#documentation-reference)

# Introduction

This document outlines that The static inventory should list all servers with correct names or IPs, organize them into groups if needed, include any required settings, and work properly when running Ansible commands.

#  Overview

An Ansible Inventory is a file that defines the list of hosts (servers or devices) that Ansible can manage. In a static inventory, the list is manually defined and does not change unless edited by a user. It contrasts with dynamic inventories that pull host data from external sources like cloud providers 

# What is static Inventory

A static inventory is the simplest and most commonly used type, especially for small or stable environments. It is a manually maintained file — usually in INI or YAML format — where you define the hostnames or IP addresses of your servers, group them logically (e.g., web_servers, db_servers), and optionally set connection variables.

# Why static Inventory

 - Simplicity and Quick Setup
 - Small or Fixed Environments
 - Easy to Track
 - Familiar Format
 - No Dependencies



#  Where to Place Inventory Files

- **Default**: `/etc/ansible/hosts` 

- **Custom Path**: You can specify a custom path using the `-i` option with Ansible commands:
  ```bash
  ansible -i <path> <command> 
   ```



# Key Steps to Follow
| Step | Title                          | Description |
|------|--------------------------------|-------------|
| 1    | **Create the Inventory File**  | Ansible uses an inventory file to define the servers you want to manage. This file can be in INI, YAML, or JSON format. Example shown below uses INI format. |
|      | **Static Inventory Example**   | ```ini<br>[web_servers]<br>web1.example.com ansible_user=ubuntu<br>web2.example.com ansible_user=ubuntu<br><br>[db_servers]<br>db1.example.com ansible_user=centos<br>db2.example.com ansible_user=centos<br><br>[api_servers]<br>10.0.0.1 ansible_user=admin<br>10.0.0.2 ansible_user=admin<br><br>[all_servers:children]<br>web_servers<br>db_servers<br>api_servers<br><br>[web_servers:vars]<br>http_port=80<br>max_clients=200<br><br>[db_servers:vars]<br>db_port=3306<br>db_user=admin<br><br>[api_servers:vars]<br>api_port=8080``` |
| 2    | **Understanding the Structure**| |
|      | Groups                         | Sections like `[web_servers]`, `[db_servers]`, and `[api_servers]` group servers for easier management. |
|      | Server Entries                 | Each entry is a hostname or IP address, optionally followed by connection variables (e.g., `ansible_user`). |
|      | Group Variables                | Group-specific settings like `http_port`, `db_port`, or `api_port` are defined for each group. |
|      | Parent Group                   | `[all_servers:children]` aggregates all groups for applying tasks across all servers. |
| 3    | **Special Settings for Ansible** | |
|      | ansible_user                   | SSH username for Ansible to connect to the target servers. |
|      | ansible_ssh_private_key_file  | *(Optional)* Path to SSH private key for authentication. |
|      | ansible_ssh_common_args       | *(Optional)* SSH arguments like disabling strict host checking. |
| 4    | **Run Ansible Commands**       | Once inventory is ready, you can target groups to run playbooks or ad-hoc commands. |
|      | Run playbook for web_servers   | ```ansible-playbook -i inventory.ini site.yml -l web_servers``` |
|      | Ping all servers               | ```ansible all -i inventory.ini -m ping``` |
|      | Ping db_servers only           | ```ansible db_servers -i inventory.ini -m ping``` |




# ansible Configuration

If you want Ansible to use a specific inventory file by default, configure `ansible.cfg`:

```ini
[defaults]
inventory = ./inventory/inventory.ini
remote_user = ubuntu
host_key_checking = False
```
# Conclusion
In conclusion, Ansible Static Inventory is an essential tool for defining and organizing the list of hosts that Ansible will manage. This manual setup method provides simplicity and control over the configuration, especially for smaller or stable environments. By grouping servers logically, assigning specific variables, and using group-based structures, static inventory enables efficient automation management.


#  Contact Information


| Name       | Email Address                |
|------------|------------------------------|
| Pravalika  | kanikarapu.pravalika.snaatak@mygurukulam.co|

##  Documentation Reference

| **Link** | **Description** |
|----------|-----------------|
| [Ansible Inventory Guide](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html) | Official documentation followed for setting up and organizing static inventories in Ansible. |


