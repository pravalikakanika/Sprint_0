

![image](https://github.com/user-attachments/assets/52505250-e374-4634-b4e1-133c9b293eb1)


|**Date**| **Version**| **Description**| **Changed By** |
|----------|---------|---------------|-----------------|
|**April 15** | v.1.0 | Initial Draft | Pravalika Kanikarapu |
|**April 19** | v.1.1 | sop_disk_ulimit.md | Pravalika Kanikarapu |
|**April 20** | v.1.2 | sop_disk_ulimit.md | Pravalika Kanikarapu |


#  **Standard Operating Procedure (SOP) for Checking Disk Usage, Mount Points, and Configuring Ulimit Settings**





#  Table of Contents

1. [Introduction](#Introduction)
2. [What is SOP](#what-is-sop)
3. [Why SOP](#why-sop)
4. [Purpose](#purpose)   
5. [ Scope](#scope)  
6. [ Prerequisites](#prerequisites)  
7. [ Procedure](#procedure)  
   - [ Step 1: Check Disk Usage](#step-1-check-disk-usage)  
   - [ Step 2: Check Mount Points](#step-2-check-mount-points)  
   - [ Step 3: Configure ulimit Settings](#step-3-configure-ulimit-settings)  
8. [ Troubleshooting](#troubleshooting)  
9. [ Contact Information](#contact-information)  
10. [ Reference](#reference)  



# Introduction

The SOP should provide steps to check disk usage, mount points, and configure ulimit settings for users and processes


# What is SOP

A Standard Operating Procedure (SOP) is a set of written instructions that describe how to perform a specific task or process consistently and efficiently. SOPs are used across various industries to ensure that operations are carried out in a standardized manner, reducing errors and ensuring quality control. 

# Why SOP

- Ensures Consistency Across Systems
- Helps in Automation and Scripting
- Speeds Up Setup and Troubleshooting

#  Purpose

This document outlines the procedures for:

- **Monitoring Disk Usage:** Ensure sufficient disk space is available to prevent system slowdowns due to excessive disk consumption.
- **Verifying Mount Points:** Confirm that all filesystem mount points are correctly configured and accessible.
- **Configuring ulimit Settings:** Set resource limits for users and processes to optimize system performance and avoid resource exhaustion.


# Scope


This SOP applies to all system administrators responsible for maintaining disk usage, mount point configurations, and resource limits.



# Prerequisites

Before proceeding with this SOP, the following prerequisites must be met:

- **Permissions:** The user must have administrative (root or sudo) access to the system.
- **Backup:** Backup critical system files before making any changes.
- **Installed Tools:** Ensure the system has the necessary utilities installed (`df`, `du`, `mount`, `ulimit`).
- **System Access:** Access to the system either via SSH or directly (local terminal).
- **Knowledge:** Basic understanding of the Linux filesystem, mount points, and resource limits.


# Procedure

### Step 1: Check Disk Usage

---

#### A. View Disk Usage Summary

Run the `df` command to check available and used disk space:

```bash
df -h
```  
**Expected Output:**



```bash

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   20G   28G  42%  /
/dev/sdb1       100G   70G   25G  75%  /mnt/data

```  

#### B.Check inode usage (important for filesystem integrity):

```bash
df -i

``` 
**Expected Output:**

```bash
Filesystem      Inodes   IUsed   IFree     IUse% Mounted on
/dev/sda1       3276800  500000  2776800   15%   /

``` 

#### C. Check detailed disk usage of directories:

```bash
du -sh /path/to/directory

```

### Step 2: Check Mount Points

### A.View all mounted filesystems:

Run the mount command to see the mounted filesystems and their mount points:

```bash
mount

```

### B. Check the /etc/fstab file to confirm the configuration of mount points:

```bash
cat /etc/fstab

```

### c. Verify the mount point:

To verify if a specific mount point is active:

```bash
df -h /mnt/data
```

### Step 3: Configure ulimit Settings
ulimit controls limits on user and process resources (file descriptors, memory, processes, etc.)

### A. View the current ulimit settings for the user:

```bash
ulimit -a
```

### B. Set or modify ulimit for the current session:

- **For example, to set the maximum number of open files to 5000:**

```bash
ulimit -n 5000
```


### c. Make permanent changes to ulimit:

- **Edit the /etc/security/limits.conf file:**

```bash
sudo nano /etc/security/limits.conf
```

   - **Add the following lines to set the limits for a user or all users:**

markdown

*               soft    nofile          5000
*               hard    nofile          10000
Apply changes by logging out and back in or restarting the system.







## Troubleshooting


| Issue                          | Solution                                                              |
|-------------------------------|-----------------------------------------------------------------------|
| Changes to ulimit not applying | Ensure PAM limits are enabled and shell is restarted                  |
| Systemd service limits ignored | Set limits in unit file and reload systemd                            |
| Disk usage high                | Use `du -sh *` to identify large directories                          |
| Mount point not found          | Check `/etc/fstab` and try remounting with `mount -a`                 |





# Contact Information


| Name       | Email Address                |
|------------|------------------------------|
| Pravalika  | kanikarapu.pravalika.snaatak@mygurukulam.co|


# Reference

| Link                                                                 | Description                              |
|----------------------------------------------------------------------|------------------------------------------|
| [https://phoenixnap.com/kb/ulimit-linux-command](https://phoenixnap.com/kb/ulimit-linux-command) | Documentation followed for this link     |
 








































