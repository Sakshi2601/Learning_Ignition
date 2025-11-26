# 📘 **Ignition Learning Notes — Day 1**

## **1️⃣ Launching Ignition Designer**

### **1. Designer Interface**

The **Ignition Designer** is the main development tool where you build Vision windows, Perspective views, UDTs, scripting, transaction groups, and more.

You learned how to:

* Launch the Designer using the **Designer Launcher**
* Log in with gateway credentials
* Create or open projects

---

## **2️⃣ Designer Launcher (3:32)**

* A small application used to open Designers connected to any gateway.
* Shows all available gateways on your PC or network.
* Lets you download the Designer launcher if missing.
* Helps connect to development or production gateways.

---

## **3️⃣ Using the Designer User Interface (3:30)**

You explored the main parts of the UI:

* **Project Browser** → shows views, windows, scripts, tags, etc.
* **Property Editor** → edit component properties.
* **Tag Browser** → view and organize tags.
* **Workspace** → main area where views/windows are edited.
* **Tools** like find/replace, events, components library.

---

## **4️⃣ Communication Modes (1:08)**

Communication modes control how the Designer interacts with live data:

* **Read/Write** → full control, real-time reading + writing.
* **Read-Only** → can read data but cannot write to PLC/tags.
* **Simulation** → safe mode for testing; doesn’t affect real devices.

Useful when working on a production gateway to avoid accidental writes.

---

## **5️⃣ Using Find and Replace (2:23)**

* Helps quickly search for tag paths, component names, scripts, text.
* Works across entire project.
* Helps in debugging or updating old project references.

---

## **6️⃣ Project Properties (3:00)**

Inside **Project → Project Properties**, you learned to configure:

* **General settings** (project name, description, edit lock)
* **Vision settings** (if using Vision)
* **Perspective settings** (page config, session settings)
* **Security** (Identity Providers, allowed roles)
* **Default resources**, custom properties, and more.

---

## **7️⃣ Versioning – Project System**

You learned how Ignition versions and organizes projects using **the project resource system**.

### **Project Inheritance (5:38)**

* You can create a **base project** and have other projects inherit from it.
* Useful for:

  * Shared components
  * Common scripts
  * Standard UI layouts
  * Reusing tag providers or styles

Child projects can override or extend resources from parent projects.

---

## **8️⃣ Production and Development Server (2:18)**

* In real companies, Ignition is often split into:

  * **Development Gateway** → you design + test projects safely.
  * **Production Gateway** → the live system used by operators.
* You design on Development, export the project, import/deploy into Production.

This avoids accidents on live systems.

---

 **End of Day 3 Notes** 
