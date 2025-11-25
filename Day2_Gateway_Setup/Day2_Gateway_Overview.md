# Ignition Learning Notes - Day 2 

## 1. Gateway Overview

* **Ignition Gateway** is the central web interface for configuration and management.
* Accessible via browser (default: `http://localhost:8088`).
* **Gateway Command-Line Utility (gwcmd):**

  * `gwcmd -p` → Puts Gateway into *Paused* mode.
  * `gwcmd -r` → *Resumes* the Gateway.
* Useful for maintenance, troubleshooting, and controlled restarts.

---

## 2. Gateway & Project Backups

### Gateway Backup

* Taken from **Config > System > Backup/Restore**.
* Creates a `.gwbk` file (includes all projects, tags, users, profiles, etc.).

### Project Backup

* Done from the **Designer**.
* File → *Export Project* → creates `.proj` file.
* Project backup contains only the selected project’s resources.

---

## 3. Licensing & Activation

* Ignition 8.1 uses online or offline activation.
* Some modules (Vision, Perspective, Reporting, MES, etc.) require **separate module licenses**.
* Activation steps:

  1. Go to **Config > Licensing**.
  2. Enter activation key.
  3. Choose online/offline activation.
* Deactivation also available for moving license to another gateway.

---

## 4. Redundancy

* Provides automatic failover between **Master** and **Backup** gateways.
* No extra license required for the redundant gateway.
* Configuration:

  * Setup redundancy roles in **Config > Redundancy**.
  * Shared data syncs automatically.
* **Database Considerations:**

  * Use an external DB (MySQL, PostgreSQL, etc.) for shared storage.
  * Avoid using local SQLite for redundancy.

---

## 5. Gateway Network & Remote Providers

### Gateway Network Overview

* Connects multiple Ignition gateways securely.
* Used for sharing tags, alarms, history, projects, and messages.

### Setting up a Gateway Network Connection

* Go to **Config > Gateway Network > Outgoing / Incoming Connections**.
* Accept connection on both gateways.
* Once connected, gateways can exchange resources.

### Remote Tag Provider

* Allows you to browse and use tags from another gateway.
* Add a new provider in **Config > Tags > Realtime Providers**.
* Select *Remote Tag Provider* and choose the connected gateway.

### Remote History Provider

* Logs history to or retrieves history from another gateway.
* Add provider in **Config > Tags > History Providers**.
* Useful in distributed architectures.

### Remote Alarms

* Allows one gateway to receive alarm state data from another.
* Set in **Alarm Journal** or **Alarm Notification** settings.

---

## Quick Summary

* Learnt gateway commands, backups, licensing, redundancy.
* Setup Gateway Network and understood Remote Providers.
* All concepts covered apply to **Ignition 8.1**.

---

**End of Day 2 Notes**
