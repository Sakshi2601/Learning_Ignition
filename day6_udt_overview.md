# **Day 6 – Tags in Ignition**

## **1. Understanding UDTs (User Defined Types)**

* A **UDT** is a **template** or **blueprint** for a group of tags.
* You define the structure **once**, and then create **many instances** of it.
* When the UDT changes, **all instances update automatically** (unless overridden).
* Useful for devices with repeated tag sets (motors, valves, pumps, tanks, etc.).

---

## **2. Creating UDT Definitions**

There are two main ways:

### **Method 1 (Manual):**

1. Right-click **Tags** → **New Data Type**
2. Add tags inside the UDT
3. Set parameters, alarms, scripts if needed
4. Click **Apply**

### **Method 2 (From OPC Browser):**

1. Open **OPC Browser**
2. Locate the device driver tags
3. Drag a folder into the Tag Browser
4. When Ignition asks, choose **Create UDT**
5. Then adjust:

   * Tag paths
   * Names
   * Parameters
   * Data types

---

## **3. Manually Creating UDT Instances**

Once a UDT exists:

1. Right-click the UDT → **New Instance**
2. Give it a name
3. Edit parameter values (e.g., device path)
4. Instance gets the **same structure** as the UDT definition

---

## **4. UDT Multi-Instance Wizard**

Used to create batches of instances quickly:

* Enter **Base Name**
* Enter **Pattern** (device1, device2, device3…)
* Enter **Count / Size**
* Set parameter values
* Click OK → many instances created at once

---

## **5. Overriding UDT Instance Properties**

Inside an instance:

* You can override **tag properties** such as:

  * OPC Item Path
  * Scaling
  * Alarms
  * Deadbands
  * Metadata

Overrides apply **only to that instance**, not the UDT definition.

---

## **6. UDT Inheritance**

* A UDT can extend another UDT (like “parent → child”).
* Child inherits all parent tags + can add more.
* Use when you want:

  * Standard base tags for all equipment
  * Specialized child types with additional features
* Example:

  * **Motor (parent)**
  * **VFD Motor (child)** with speed feedback tags

---

## **7. Nested UDTs**

* A UDT can contain **another UDT** inside it.
* Used in large projects where devices contain sub-components.

### **Making Nested UDTs Dynamic (Using Parameters)**

Inside UDTs, parameters allow dynamic OPC paths:

Example parameter:

```
{DeviceName}
```

Using it in OPC path:

```
ns=1;s[{DeviceName}]/Motor/Status
```

### **Parameter Scope (Local vs Global)**

* **Local to each instance**

  * Every instance can have its own parameter values.
* Parameters **belong only to that UDT instance**, not global in the project.
* If a nested UDT exists, it gets:

  * Its own parameters
  * Access to parent parameters (using `{ParentParam}` syntax)

---

## **8. Tag Groups Overview**

Tag Groups control **how often** a tag reads from OPC or executes.

Edit:

* Right-click tag group folder → **Edit Tag Group**
* Or create a new tag group

Important properties:

* **Mode:** Direct, Driven, Leased
* **OPC Data Mode:** Subscribed or Polled
* **Rate** (ms)

### **Modes**

1. **Direct**

   * Reads at a fixed rate (ex: 1000 ms)

2. **Driven**

   * Reads only when a condition is TRUE
   * Used for event-based reads

3. **Leased**

   * Reads fast when visible, slow when not visible

---

## **9. Driven Tag Group (Rate or Event-Based)**

Steps:

1. Create a tag group
2. Set Mode = **Driven**
3. Give **Fast Rate** (1000 ms)
4. Give **Slow Rate** (60000 ms)
5. Add driving expression tag
6. Set comparison:

   * Expression result = **1 → Fast Rate**
   * Expression result = **0 → Slow Rate**

Useful for:

* Reading fast when machine running
* Reading slow when machine off

---

## **10. Leased Tag Group (How It Works)**

A **Leased Tag Group** changes scan rate based on tag usage/visibility.

### **How it works**

* If a tag is **used in a client/UI** (visible), it updates at **fast rate**
* If not used, it updates at **slow rate**

Example:

* Fast Rate: **1000 ms**
* Slow Rate: **10000 ms**

When a Perspective or Vision screen opens that contains the tag:

* Tag switches to **fast** to give real-time data
  When user closes that screen:
* Tag switches to **slow** to save CPU and bandwidth

### **Used for**

* Large PLCs
* Thousands of tags
* HMI screens that are not always open
* Reducing load on PLC connections

---

