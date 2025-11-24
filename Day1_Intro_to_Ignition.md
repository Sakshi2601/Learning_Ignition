# 📘 **Ignition Learning Notes — Day 1**

## **1. What’s New in Ignition 8**

Ignition 8 introduced several major improvements, especially in visualization and security.

### ✅ **Perspective Module**

* A new web-based visualization system.
* Allows you to access projects from **any web browser**, mobile, tablet, or desktop.
* Fully **responsive** — layouts automatically adjust to screen sizes.
* Projects are designed using **Views**, which contain:

  * Components
  * Bindings
  * Parameters
  * Style classes
* You can use **style classes** for reusable UI styling.

### ✅ **Enhanced Security**

* Ignition 8 introduced **Identity Providers (IdP)** for modern authentication:

  * Username/Password
  * SAML
  * OAuth
* Perspective sessions can require authentication.
* Role-based security is easier and more powerful.

### ✅ **Tag Browser Improvements**

* Better organization of:

  * Standard Tags
  * UDTs
  * OPC Tags
  * Memory Tags
* Cleaner UI with faster tag imports/exports
* Clear separation between **project resources** and **gateway-level resources**

---

## **2. Introduction to Ignition**

**Ignition is an industrial software platform** used to build:

* HMI (Human-Machine Interface)
* SCADA (Supervisory Control And Data Acquisition)
* MES (Manufacturing Execution Systems)

### What it does:

* Connects to PLCs, sensors, and industrial devices
* Collects, stores, and analyzes real-time data
* Builds dashboards, alarms, charts, and control screens
* Runs on Windows, Linux, and macOS
* Uses web-based clients (Perspective) or desktop clients (Vision)

Short definition:
👉 *Ignition is a unified industrial platform that connects devices, stores data, and provides tools to build SCADA/HMI/MES applications.*

---

## **3. About Ignition Modules**

Ignition is modular. You install only what you need.

Important modules:

### **Visualization**

* **Perspective** – web-based UI
* **Vision** – desktop clients

### **Database & Logic**

* **SQL Bridge** – Transaction Groups
* **Scripting** – Python (Jython) scripting
* **Reporting** – auto-generated reports
* **Sequential Function Charts (SFC)** – graphical automation logic

### **Connectivity**

* **OPC UA Module** – PLC communication
* **Drivers** (Allen-Bradley, Siemens, Modbus, etc.)

### **Enterprise**

* **EAM (Enterprise Administration Module)** – central management
* **Tag Historian Module** – store tag values over time
* **Alarm Notification Module** – email/SMS/voice alerts

Ignition is like an app store — install modules you need.

---

## **4. Ignition System Architecture**

Ignition can be deployed in multiple ways:

### **Standard Architecture**

* One gateway
* Connects to PLCs
* Runs clients
* Stores tag history and alarms

### **Scaled-Out Architecture**

* Separate **Front-End Gateway** → UI, Perspective, Vision
* Separate **Back-End Gateway** → Tag Historian, Alarms, Databases
* Reduces load and improves performance

### **Multi-Site Architecture**

* Multiple sites (factories)
* Each with local gateways
* Connected to a **central corporate gateway** for reporting and control
* Used in large enterprises

### **General Flow**

PLC → OPC UA → Ignition Gateway → Database / Clients / Perspective

---

## **5. Installing Ignition on Windows**

Steps to install Ignition:

1. Go to the official Inductive Automation website
2. Download Ignition for Windows
3. Run the installer (Next → Next → Finish)
4. Gateway starts automatically at

   ```
   http://localhost:8088
   ```
5. Set username, password, and finish initial setup
6. You can **upgrade modules later** by:

   * Going to **Config → Modules**
   * Uploading module .modl files
   * Installing licensed or trial versions

Installation is very easy — just download → install → run.
