# **Day 5 — Tags in Ignition**

### *Understanding Tags and Tag Types in Ignition*

## **1. What are Tags in Ignition?**

Tags are **data points** inside Ignition.
They represent values from:

* PLCs
* OPC servers
* Expressions
* Memory values
* Database queries
* Gateway info (system tags)

Tags = variables used everywhere in Ignition (Vision, Perspective, scripts, alarms, history).

---

## **2. Tag Providers**

A *Tag Provider* is simply a **container/group** of tags.

Types:

* **default provider** (comes with every project)
* **custom provider** (you can create your own)
* **realtime providers**
* **historical providers**

Purpose:

* Organize tags
* Keep different projects or departments separate

---

## **3. Importing & Exporting Tags**

You can **export** or **import** tags as:

* JSON
* XML

Useful for:

* Backup
* Moving tags from dev to production
* Copy tags between projects

---

## **4. Tag Diagnostics**

If a tag has a problem (bad path, connection error):

* Tag Browser shows a **red error icon**
* Tag Diagnostics panel explains the issue
  (e.g., bad quality, bad OPC address, gateway disconnected)

---

## **5. Tag Editor**

Tag Editor allows you to configure tag properties.

Main sections:

* **Basic** — Name, datatype, OPC path
* **Value** — Read/write value
* **Numeric** — Formats, engineering units
* **Scripting** — Run scripts on value change
* **Alarm** — Add alarms
* **History** — Enable historian
* **Security** — Permission to read/write
* **Custom** — Add your own metadata fields

---

## **6. Tag Quality & Overlays**

Tag has two states:

* **Good** → Data is valid
* **Bad** → Error (bad OPC path, device fault, etc.)

Vision/Perspective show **overlays** (red box, slash, etc.) for bad quality.

---

## **7. Tag Scaling (Simple Explanation)**

Tag scaling converts **raw PLC values** into **engineering values**.

Example:
PLC sends **0–2000**, but you want it displayed as **0–100%**.

Linear scaling does:

```
Raw Low → Raw High
Scale Low → Scale High
```

Example:

```
Raw Low = 0  
Raw High = 2000  
Scale Low = 0  
Scale High = 100  
```

So PLC value **2000 becomes 100%**,
PLC value **1000 becomes 50%**.

Other scaling types:

* Linear
* Square root
* Exponential

Used for sensors like flow transmitters, pressure sensors, etc.

---

## **8. Browsing OPC Tags**

Dragging tags from the OPC Browser works, but:

* Not recommended for large systems
* Sometimes brings unnecessary folders
* Better to create OPC tags **manually**

---

## **9. Creating OPC Tags Manually**

Steps:

1. In Tag Browser → Add Tag → OPC Tag
2. Set:

   * Tag Name
   * Data Type
   * OPC Server
   * **OPC Item Path** (example: `ns=1;s=[PLC]LevelPV`)
3. Press OK

This gives you clean, controlled tags.

---

## **10. Addressing Bits (Short Explanation)**

PLC gives a **full integer word** (e.g., 16 bits).

If you want to **write to ONE BIT**, you must create a Boolean tag for that bit.

Example:
OPC path:

```
[PLC]LevelPV
```

To access bit 1:

```
[PLC]LevelPV.1
```

Then change datatype to **Boolean**.

Why?

* Writing an entire integer risks overwriting other bits
* Writing to a single Boolean is safe

Some PLCs (like MicroLogix) let you expand bits in the OPC Browser.

---

## **11. Device Diagnostic Tags**

These tags automatically appear under devices.

They show:

* Connection quality
* Last communication time
* Device faults
* Opc server status

Useful for troubleshooting PLC/device connectivity.

---

## **12. Memory Tag**

A tag stored **inside Ignition**, not coming from PLC.

Used for:

* Testing
* Temporary variables
* Operators entering values
* Script storage

Types:
Boolean, Integer, Float, String, Dataset, etc.

---

## **13. Derived Tag**

A tag that **maps** to another tag but can modify read/write.

Example:

* Read raw PLC value
* Scale it
* Write back using formula

Useful for:

* Unit conversions
* Write validation
* Custom logic between tag and PLC

---

## **14. Reference Tag**

A tag that simply **points** (references) another tag’s value.

Example:

```
Machine1/Speed → MachineOverview/Speed
```

No need to duplicate tags.

---

## **15. Expression Tag**

Tag whose value is calculated using an **expression**

Example:

```
({Temp1} + {Temp2}) / 2
```

or

```
if({Level} > 80, "High", "Normal")
```

Used for calculations, logic, strings, conditions.

---

## **16. Query Tag**

Tag that runs a SQL query and returns the result.

Example:

```
SELECT COUNT(*) FROM orders WHERE status='pending'
```

Used for:

* Dashboard counters
* Database values into tags

---

## **17. System Tags (Short, Clear Explanation)**

System Tags = built-in tags that provide information about:

### **Gateway**

* Uptime
* Performance (memory / CPU)
* Redundancy
* Projects
* Alarms

### **Clients (Vision/Designer)**

* Username
* Hostname
* Roles
* Time
* Window info

Important points:

* You **cannot create or edit** system tags
* They are **read-only**
* Vision client system tags differ from gateway tags
* Perspective does NOT use client tags → it uses Session Props

---

## **18. Client Tags**

These belong to **Vision Clients only**, NOT Perspective.

Behaviors:

* Each client has its **own value**
* Used for per-user runtime data
* Example: selected line, operator input, window settings
* Stored temporarily in client memory

---

*End of Day 5 Notes*
