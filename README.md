# Sprint_0


**Standard Operating Procedure (SOP) for Checking Disk Usage, Mount Points, and Configuring Ulimit Settings**


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



```bash

Filesystem      ..... Size .. Used .. Avail . Use% . Mounted on
/dev/sda1       ..... 50G  .. 20G  .. 28G   . 42%  . /
/dev/sdb1       ..... 100G .. 70G  .. 25G   . 75%  . /mnt/data




























