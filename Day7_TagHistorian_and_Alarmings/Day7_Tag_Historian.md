# **Day 7 – Tag Historian & Tag History Gateway Settings**

## **(i) Tag Historian**

### **1. Configuring Tag History (Full Process)**

**Tag Historian** stores tag values in a database so you can view trends, charts, and analysis.

**Steps to Configure Tag History:**

1. **Set up a Database Connection**

   * Go to **Gateway → Config → Databases → Connections**
   * Create a SQL database connection (MySQL, MSSQL, PostgreSQL, etc.).
   * Make sure status is **Valid**.

2. **Enable the Tag History Provider**

   * Go to **Gateway → Config → Tags → History**
   * Default provider = **DB Default**, or you can create a new history provider.
   * Select your database connection.

3. **Enable History on a Tag**

   * Open Designer → **Tag Browser**
   * Right-click any tag → **Edit Tag**
   * Go to the **History** tab.
   * Check **Store history for this tag**.
   * Choose:

     * **Provider**
     * **Sample Mode** (On Change / Periodic / Tag Group Rate)
     * **Deadband**
     * **Storage Type** (Full / Minimal etc.)

4. **Save Tags** → History starts logging immediately.

---

### **2. Add History to Tags Inside a UDT**

When you enable history at the **UDT definition level**, all instances inherit the history settings.

**Steps:**

1. Open Designer → **Tag Browser**
2. Open **Data Types** → Select your UDT
3. Choose the **member tag** inside UDT
4. Open **Tag Editor → History**
5. Enable **Store history for this tag**
6. Save UDT definition

➡ All UDT instances will automatically log history for those tags.

*(You can override history settings per-instance if needed.)*

---

### **3. Easy Chart (To Show Tag History)**

Easy Chart is used in **Vision** to view historical trends.

**Using Easy Chart:**

1. Open Designer → **Vision → Windows**
2. Drag **Easy Chart** component onto the window
3. Go to **Easy Chart Customizer**
4. Add Pen:

   * **Tag Historian Pen**
   * Browse your tag
5. Run Vision Client → the chart shows live + history data
6. You can zoom, pan, change modes, etc.

➡ In **Perspective**, history is shown using the **Time Series Chart** (not Easy Chart).

---

---

## **(ii) Tag History Gateway Settings**

Go to **Gateway → Config → Tags → History** to configure advanced settings.

### **1. Data Partitioning and Pruning**

#### **Data Partitioning**

* Historical data is stored in **partitions** (similar to separate tables for different date ranges).
* Default partition size: **1 month**.
* Benefits:

  * Faster query performance
  * Easier pruning
  * Cleaner database maintenance

You can set:

* Partition size (1 week / month / custom)

#### **Pruning**

* Automatically deletes old history after a certain time.
* Example:

  * Keep only last **6 months** of data.
* Prevents large database growth.

You can configure:

* **Enable pruning**
* **Max age** (days/months/years)

---

### **2. Tag History Splitter**

Tag History Splitter lets you store the same tag history in **two places at once**.

Example uses:

* Store high-resolution data in local DB
* Store backup data in a remote central server
* Store into TimescaleDB + MySQL simultaneously

Steps:

1. Go to **Gateway → Config → Tags → History → Providers**
2. Create new provider → **Tag History Splitter**
3. Add multiple history providers
4. Enable for tags

➡ When a tag logs history, the splitter writes the same record into all configured providers.

---

**End of Day 7 Notes**
