

![image](https://github.com/user-attachments/assets/52505250-e374-4634-b4e1-133c9b293eb1)


## 📂 Document Info

| Author          | Created On  | Version   | Last Updated By | Last Edited On |
|-----------------|-------------|-----------|------------------|----------------|
| Pravalika  | 2025-04-14  | Version 1 |Pravalika | 2025-04-16     |


## 🗂️ Table of Contents

1. [Purpose](#purpose)  
   1.1 [Monitoring Disk Usage](#monitoring-disk-usage)  
   1.2 [Verifying Mount Points](#verifying-mount-points)  
   1.3 [Configuring ulimit Settings](#configuring-ulimit-settings)  

2. [Scope](#scope)  

3. [Prerequisites](#prerequisites)  
   3.1 [Permissions](#permissions)  
   3.2 [Backup](#backup)  
   3.3 [Installed Tools](#installed-tools)  
   3.4 [System Access](#system-access)  
   3.5 [Knowledge](#knowledge)  

4. [Procedure](#procedure)  
   4.1 [Step 1: Check Disk Usage](#step-1-check-disk-usage)  
      4.1.1 [View Disk Usage Summary](#view-disk-usage-summary)  
      4.1.2 [Check Inode Usage](#check-inode-usage)  
      4.1.3 [Check Detailed Disk Usage of Directories](#check-detailed-disk-usage-of-directories)  
   4.2 [Step 2: Check Mount Points](#step-2-check-mount-points)  
      4.2.1 [View All Mounted Filesystems](#view-all-mounted-filesystems)  
      4.2.2 [Check the /etc/fstab File](#check-the-etc-fstab-file)  
      4.2.3 [Verify the Mount Point](#verify-the-mount-point)  
   4.3 [Step 3: Configure ulimit Settings](#step-3-configure-ulimit-settings)  
      4.3.1 [View Current ulimit Settings](#view-current-ulimit-settings)  
      4.3.2 [Set or Modify ulimit for the Current Session](#set-or-modify-ulimit-for-the-current-session)  
      4.3.3 [Make Permanent Changes to ulimit](#make-permanent-changes-to-ulimit)  

5. [Troubleshooting](#troubleshooting)  

6. [Contact Information](#contact-information)  

7. [Reference](#reference)

















## 🗂️ Purpose

This document outlines the procedures for:

- **Monitoring Disk Usage:** Ensure sufficient disk space is available to prevent system slowdowns due to excessive disk consumption.
- **Verifying Mount Points:** Confirm that all filesystem mount points are correctly configured and accessible.
- **Configuring ulimit Settings:** Set resource limits for users and processes to optimize system performance and avoid resource exhaustion.


## 🔍 Scope


This SOP applies to all system administrators responsible for maintaining disk usage, mount point configurations, and resource limits on [list of systems or servers].



## 🧑‍💻 Prerequisites

Before proceeding with this SOP, the following prerequisites must be met:

- **Permissions:** The user must have administrative (root or sudo) access to the system.
- **Backup:** Backup critical system files before making any changes.
- **Installed Tools:** Ensure the system has the necessary utilities installed (`df`, `du`, `mount`, `ulimit`).
- **System Access:** Access to the system either via SSH or directly (local terminal).
- **Knowledge:** Basic understanding of the Linux filesystem, mount points, and resource limits.


## 📋 Procedure

### ✅ Step 1: Check Disk Usage

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

### ✅ Step 2: Check Mount Points

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

### ✅ Step 3: Configure ulimit Settings
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







## 🧯 Troubleshooting


| Issue                          | Solution                                                              |
|-------------------------------|-----------------------------------------------------------------------|
| Changes to ulimit not applying | Ensure PAM limits are enabled and shell is restarted                  |
| Systemd service limits ignored | Set limits in unit file and reload systemd                            |
| Disk usage high                | Use `du -sh *` to identify large directories                          |
| Mount point not found          | Check `/etc/fstab` and try remounting with `mount -a`                 |





## 📧 Contact Information


| Name       | Email Address                |
|------------|------------------------------|
| Pravalika  | kanikarapu.pravalika.snaatak@mygurukulam.co|


## 📚 Reference

| Link                                                                 | Description                              |
|----------------------------------------------------------------------|------------------------------------------|
| [https://phoenixnap.com/kb/ulimit-linux-command](https://phoenixnap.com/kb/ulimit-linux-command) | Documentation followed for this link     |







































