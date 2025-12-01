# Day 8: Windows in Ignition (Vision)

## **1. Anatomy of a Window**

A Vision Window is the main space where you place components (buttons, labels, charts). It includes:

* **Root Container**: The base, main container for all components.
* **Other Containers**: Tab, Collapsible, Coordinate, etc.
* **Components**: Visible objects placed on the window.
* **Event Scripts**: Used to control logic.

---

## **2. Window Types**

Ignition Vision has 3 main window types:

### **❶ Main Window**

* Your primary screens.
* Only one should be open at a time.

### **❷ Popup Window**

* Opens on top of other windows.
* Used for dialogs, forms, details.

### **❸ Docked Window**

* Sticks to a screen edge (top/bottom/left/right).
* Used for navigation bars, headers, alarms.

---

## **3. Window Properties**

Important properties in the Vision Window:

* **Size** – height/width of window
* **Start Maximized** – opens window in full screen
* **Border / Titlebar options**
* **Layer** – which window appears on top
* **Parameters** – used for passing values (dynamic windows)

---

## **4. Open Static Window(s) on Startup**

Static windows = no parameters.

To open them automatically:

1. Go to **Project Properties** > **Client Events** > **Startup**.
2. Add script:

```
system.nav.openWindow("MainWindow")
```

3. Or use **Startup Windows** setting.

---

## **5. Open Dynamic Window(s) on Startup**

Dynamic windows use parameters.

Example:

```
system.nav.openWindow("MotorDetails", {"MotorID": 5})
```

Used when you want a window to show different data based on parameters.

---

## **6. Docked Windows – Order Precedence**

If multiple docked windows exist:

* **North (Top)** has highest priority
* Then **South**, **East**, and **West**
* You can set **overlap** or **avoid** mode

Docked windows can also be set as:

* **Auto-hide**
* **Resizeable**
* **Show/Hide programmatically**

Example hide/show:

```
system.nav.closeWindow("NavigationBar")
system.nav.openWindow("NavigationBar")
```
