

![image](https://github.com/user-attachments/assets/52505250-e374-4634-b4e1-133c9b293eb1)




| Author        | Date       | Version | Review Level   | Reviewer Name        |
|---------------|------------|---------|----------------|----------------------|
| pravalika Kanikarapu  | April 20   | v1.1    | Pre-Reviewer   | Priyanshu            |
| pravalika Kanikarapu  | April 24   | v2.1    | L0             | Khushi Malothra      |
| pravalika Kanikarapu  |            |         | L1             | Rishabh Sharma       |
| pravalika Kanikarapu  |            |         | L2             | piyush Upadhyay      |



#  **SOP For Checking Disk Usage,Mount Points,and Configuring Ulimit**




#  Table of Contents

1. [Introduction](#Introduction)
2. [Purpose](#purpose)   
3. [ Scope](#scope)  
4. [ Prerequisites](#prerequisites)  
5. [ Procedure](#procedure)  
   - [ Step 1: Check Disk Usage](#step-1-check-disk-usage)  
   - [ Step 2: Check Mount Points](#step-2-check-mount-points)  
   - [ Step 3: Configure ulimit Settings](#step-3-configure-ulimit-settings)  
6. [ Troubleshooting](#troubleshooting)  
7. [Conclusion](#conclusion)
8. [ Contact Information](#contact-information)  
9. [ Reference](#reference)  



# Introduction

The SOP provides steps to check disk usage, mount points, and configure ulimit settings for users and processes



#  Purpose

This document outlines the procedures for:

- **Monitoring Disk Usage:** Ensure sufficient disk space is available to prevent system slowdowns due to excessive disk consumption.
- **Verifying Mount Points:** Confirm that all filesystem mount points are correctly configured and accessible.
- **Configuring ulimit Settings:** Set resource limits for users and processes to optimize system performance and avoid resource exhaustion.





# Prerequisites

| Requirement     | Description                                                                 |
|----------------|-----------------------------------------------------------------------------|
| **Permissions** | User must have administrative (root or sudo) access to the system.         |
| **Installed Tools** | Ensure utilities like `df`, `du`, `mount`, and `ulimit` are available. |                    |
| **Knowledge**    | Basic understanding of Linux filesystem, mount points, and resource limits.|



# Procedure

### Step 1: Check Disk Usage


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

**Expected Output:**
```bash
1.5G    /path/to/directory
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

1.  **Edit the /etc/security/limits.conf file:**

```bash
sudo nano /etc/security/limits.conf
```

   2. **Add the following lines to set the limits for a user or all users:**



 ```bash               soft    nofile          5000 ```

 ```bash               hard    nofile          10000 ```

Apply changes by logging out and back in or restarting the system.







# Troubleshooting


| Issue                          | Solution                                                              |
|-------------------------------|-----------------------------------------------------------------------|
| Changes to ulimit not applying | Ensure PAM limits are enabled and shell is restarted                  |
| Systemd service limits ignored | Set limits in unit file and reload systemd                            |
| Disk usage high                | Use `du -sh *` to identify large directories                          |
| Mount point not found          | Check `/etc/fstab` and try remounting with `mount -a`                 |



# Conclusion 
This SOP provides a structured and reliable approach for system administrators to monitor disk usage, verify mount point configurations, and manage system resource limits using ulimit on Ubuntu systems. 

# Contact Information


| Name       | Email Address                |
|------------|------------------------------|
| Pravalika  | kanikarapu.pravalika.snaatak@mygurukulam.co|


# Reference

| Link                                                                 | Description                              |
|----------------------------------------------------------------------|------------------------------------------|
| [https://phoenixnap.com/kb/ulimit-linux-command](https://phoenixnap.com/kb/ulimit-linux-command) | Documentation followed for this link     |
 








































