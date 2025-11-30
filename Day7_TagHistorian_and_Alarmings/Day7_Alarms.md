# **Day 7 – Alarms in Ignition**

*Ignition Alarming, Journals, Notification Profiles & Pipelines*

---

## **1. Configuring an Alarm**

* Alarms are configured **on tags** in the Tag Editor.
* Choose an **alarm type** (e.g., High, Low, Equal, Bit-State).
* Set:

  * **Setpoint** (threshold)
  * **Mode** (above/below/set)
  * **Priority**
  * **Label**
  * **Notes**
  * **Display path** for UI grouping
* Alarms appear in the **Alarm Status** and **Alarm Journal** components.

---

## **2. Dynamic Setpoint for Alarm**

* Instead of a fixed setpoint, bind the **Setpoint** property to:

  * Another tag
  * UDT parameter
  * SQL query
  * Expression
* Example: `High Setpoint = {Tank/Setpoints/HighLevel}`
* This makes alarms flexible and data-driven.

---

## **3. Configure Alarm in a UDT**

* Open UDT Definition → Add a tag → Add alarm inside that tag.
* All UDT instances automatically inherit the alarm.
* Best practice for motors, tanks, pumps, etc.

---

## **4. UDT Alarm Dynamic Setpoint**

* Use **UDT Parameters** to set unique setpoints per instance.
* Bind alarm setpoint like:

  ```
  {this}/../HighLimit
  or
  {UDTParam.HighLevelLimit}
  ```
* Each instance has different setpoints while sharing same alarm structure.

---

## **5. Multiple Alarms on a Tag**

* A single tag can have **multiple alarm conditions**, such as:

  * High
  * High-High
  * Low
  * Low-Low
  * Device failed
* All alarms are evaluated independently.

---

## **6. Alarm Grouping**

* Use **Display Path** or **Label** to group alarms for display:

  * Example: `Boiler 1/Temperature`
* Alarm Status component uses these groups for filtering and organizing.

---

# **Alarm Journal Profile**

Stores **historical alarm events** (active, cleared, acknowledged).
You configure:

* Name
* Database connection
* Storage settings
* Pruning

Journal data appears in the **Alarm Journal Component**.

---

# **Alarm Status Component**

Shows **active & unacknowledged alarms**.

### **General Filtering**

* Filter by:

  * Priority
  * Source
  * State (Active/Ack/Cleared)
  * Display path

### **Filter on Associated Data**

* You can add custom **Associated Data** to alarms (e.g., Area = "Line1").
* Alarm Status can filter using these values.

### **Row Styles**

* Customize colors/styles based on:

  * Priority
  * State
  * Custom logic

---

# **Alarm Journal Component (Historical View)**

### **Filter on Date Range**

* Pick a start & end timestamp to view past alarms.

### **General Filtering**

* Same as Alarm Status but applied to historical data.

### **Filter on Associated Data**

* Useful for filtering alarms related to:

  * Machine line
  * Batch number
  * Area

### **Row Styles**

* Apply color/formatting for clarity.

---

# **Notification Profiles**

## **1. Email Notification Profile**

* Uses SMTP server
* Sends alarm messages to email recipients
* Supports HTML templates & custom body text

## **2. SMS Notification Profile**

* Uses SMS provider or modem
* Sends alarm messages as SMS text

## **3. VOIP Notification Profile**

* Uses SIP server
* Notifies through voice calls
* Plays TTS (text-to-speech) messages to operators

---

# **Notification Users**

* Configure users that can receive notifications
* Each user has:

  * Contact info (email, phone, SIP)
  * Schedules
  * On-call groups

---

# **User Schedules**

Defines when a user is **available** to receive alarms.
Examples:

* Day shift (9 AM – 5 PM)
* Night shift
* Weekends only

---

# **On-Call Rosters**

* Group of users assigned to be notified
* Follows rules:

  * First available user
  * All users
  * Rotation

---

# **Alarm Pipeline Overview**

Pipelines determine **how** notifications flow.

## **Simple Pipeline**

* Basic flow:

  * Alarm → Notify block → End

## **Pipeline Blocks**

* **Switch** – conditional routing
* **Split** – send to multiple paths
* **Notification** – email/sms/voip
* **Delay** – wait before sending again
* **Escalate** – notify next group

## **Pipeline Status**

Shows real-time flow of alarms through the pipeline.

## **Adding Pipelines to Tags**

* In the alarm settings, set:

  * **Notification Mode = Pipeline**
  * Choose pipeline name

---

# **Dynamic Rosters**

* Roster updated automatically based on:

  * Shift schedules
  * Associated data
  * Runtime conditions

---

## **Pipeline – Filter on Alarm Priority**

* Route only high-priority alarms to specific recipients.

Example:

* Priority ≥ High → Supervisor
* Priority Low → Operator

---

## **Pipeline – Filter on Associated Data**

* Filter alarms by:

  * Machine type
  * Area
  * Batch

---

## **Pipeline – Escalation**

* If no one acknowledges in X minutes:

  * Escalate to next group
  * Send voice call
  * Send SMS

---

**End of Day 7 Notes**

