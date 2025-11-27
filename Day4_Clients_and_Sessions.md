# Ignition Learning - Day 4 

## ** Clients and Sessions - Overview**

In Ignition, visualization for HMI and SCADA systems is mainly done through **Vision Clients** and **Perspective Sessions**. These are the interfaces operators use to monitor and control processes.

---

## **Vision Clients**

Vision Clients are desktop-based applications used to display Vision module projects.

### **Vision Client Launcher**

* Used to launch Vision projects installed on the Gateway.
* Allows adding multiple project shortcuts.

### **Windowed Option**

* Launches the client in a normal application window.
* Allows resizing and moving like standard software.

### **Full Screen Option**

* Opens the client in full-screen mode for operator/industrial environments.
* Removes distractions and prevents accidental closing.

### **Multi-Monitor Clients**

* Used when the project needs to span across multiple screens.
* Useful for control rooms or dashboards.

### **Locate All Opened Windows in Client**

* Helps find windows that are open but not visible on screen.
* Good for debugging layouts.

### **Hiding Client Menu Bar**

* Used for a cleaner UI and to restrict operator access.

---

## **Vision Client Properties**

Vision has several client-side settings that affect usability and behavior.

### **About Client Updates**

* Whenever the project is saved in Designer, clients detect changes and refresh automatically.

### **Setting up Client Auto Login**

* Automatically logs in users without requiring credentials.
* Useful for kiosk or low-security environments.

### **Setting Client Minimum Size**

* Defines the smallest size allowed for the client window.
* Prevents UI breaking due to resizing.

### **Customizing Client Login Screen**

* Change images, colors, and layout of the login interface.
* Helps in branding and better operator experience.

### **Using Touchscreen Mode**

* Enlarges UI elements for touch-based displays.

### **Setting Project Polling Base Rate**

* Controls how frequently the client polls the gateway for tag changes.
* Higher polling → more real-time updates but more load.

---

## **Perspective Sessions**

Perspective is web-based and fully responsive.

### **Launching a Session**

* Open through any web browser.
* URL-based access makes it easy to deploy across devices.

### **The Ignition Perspective App**

* Mobile app for Android/iOS.
* Allows native app-like usage of Perspective projects.
* Supports offline caching and mobile-friendly features.

---

## **Perspective Session Properties**

These settings define how sessions behave.

### **Session Update Notifications**

* Notifies users when a project update is available.
* Users can refresh the session to load new changes.

---
**End of Day 4 Notes**

