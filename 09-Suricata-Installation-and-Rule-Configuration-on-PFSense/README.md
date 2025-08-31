# Suricata Installation and Rule Configuration on PFSense

### Project Overview
This lab focuses on `Suricata` (`Intrusion Detection System`/`Intrusion Prevention System`) installation and configuration on a `pfSense` `firewall`. Network traffic monitoring and security are explored through applying rule sets, analyzing alerts, and ensuring threat protection.

### Goals
* Install and configure `Suricata` on a `pfSense firewall`.
* Apply rule sets to monitor and secure network traffic.
* Analyze `Suricata` alerts to identify potential threats.
* Ensure protection against network threats using `Suricata`.

### Task Summary
* **Task 1:** Accessing `PfSense` & `Suricata` Installation from the `Package Manager`: Gained access to `pfSense` using the desktop shortcut and then explored the `pfSense System Package Manager` to install `Suricata`.
* **Task 2:** Global Settings Navigation & `ETOpen` Rules Configuration: Accessed `Suricata`'s `Global Settings` to configure `ETOpen Emerging Threats` rules using a custom `URL`.
* **Task 3:** `Suricata` Rules Update & Interface Creation: Updated `Suricata` rules for current threat definitions and established a new `Suricata` monitoring interface.
* **Task 4:** `WAN Categories` Configuration & `Pass List` Creation: Defined `WAN Categories` for `Suricata`'s rule set loading and created a new `Suricata pass list`.
* **Task 5:** `Suricata` Interface Start & `Nmap` Scan Execution: Initiated the configured `Suricata` interface and performed an `Nmap` scan on the `pfSense IP`.
* **Task 6:** Review `Suricata` Alerts: Examined `Suricata`'s Alerts section to observe `IDS`-generated alerts from the `Nmap` scan.

### Step-by-Step Guide

---

### Task 1: Accessing PfSense & Suricata Installation from the Package Manager

![Figure 1 - Accessing PfSense & Suricata Installation](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/09-Suricata-Installation-and-Rule-Configuration-on-PFSense/images/Figure01_Accessing_PfSense.png)

1. Accessed `pfSense` using the desktop shortcut and logged in with username `admin` and password.
2. Navigated to `System > Package Manager`, clicked on `Available Packages`, searched for `Suricata`, and installed it.
3. Confirmed installation on the confirmation page, verifying a success message.

![Figure 2 - Suricata Installation Verified](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/09-Suricata-Installation-and-Rule-Configuration-on-PFSense/images/Figure02_Suricata_Installation_Verified.png)

### Task 2: Global Settings Navigation & ETOpen Rules Configuration

![Figure 3 - Global Settings Navigation & ETOpen Rules Configuration](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/09-Suricata-Installation-and-Rule-Configuration-on-PFSense/images/Figure03_Global_Settings_Navigation.png)

1. Navigated to `Services > Suricata` and selected `Global Settings`.
2. Ticked `"Install ETOpen Emerging Threats rules"` and `"Use a Custom URL for ETOpen downloads,"` inserting the provided `URL https://rules.emergingthreats.net/open/suricata-5.0/emerging.rules.tar.gz` (a free open-source Emerging Threats Open collection of rules for `IDS` like `Suricata`).
3. Kept all other default settings and clicked `Save` at the bottom of the page.

![Figure 4 - ETOpen Rules Configuration Verified](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/09-Suricata-Installation-and-Rule-Configuration-on-PFSense/images/Figure04_ETOpen_Rules_Configuration_Verified.png)

### Task 3: Suricata Rules Update & Interface Creation

![Figure 5 - Suricata Rules Update & Interface Creation](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/09-Suricata-Installation-and-Rule-Configuration-on-PFSense/images/Figure05_Suricata_Rules_Update.png)

1. In `Suricata`, navigated to `Updates` and clicked `Update`, ensuring completion and `MD5` signature presence.
2. Navigated to `Interfaces`, clicked `Add`, and created a new interface to monitor (kept default settings).
3. Clicked `Save` at the bottom of the page.

![Figure 6 - Interface Creation Verified](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/09-Suricata-Installation-and-Rule-Configuration-on-PFSense/images/Figure06_Interface_Creation_Verified.png)

### Task 4: WAN Categories Configuration & Pass List Creation

![Figure 7 - WAN Categories Configuration & Pass List Creation](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/09-Suricata-Installation-and-Rule-Configuration-on-PFSense/images/Figure07_WAN_Categories_Configuration.png)

1. Configured `WAN Categories` by selecting all rule sets to load at startup, then saved changes.
2. In `Suricata`, navigated to `Pass Lists`, clicked `Add`, and created a new pass list (kept default settings).
3. Clicked `Save` at the bottom of the page.

![Figure 8 - Pass List Creation Verified](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/09-Suricata-Installation-and-Rule-Configuration-on-PFSense/images/Figure08_Pass_List_Creation_Verified.png)

### Task 5: Suricata Interface Start & Nmap Scan Execution

![Figure 9 - Suricata Interface Start & Nmap Scan Execution](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/09-Suricata-Installation-and-Rule-Configuration-on-PFSense/images/Figure09_Suricata_Interface_Start.png)

1. In `Suricata`, navigated to `Interfaces` and started the previously created interface, ensuring successful startup with a green indicator.
2. Waited `2-3 minutes` for the system to begin monitoring and securing the interface.
3. Opened `CMD` and executed an `Nmap` scan on the `IP address` of `pfSense`, then waited for the scan to finish.

![Figure 10 - Nmap Scan Execution Verified](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/09-Suricata-Installation-and-Rule-Configuration-on-PFSense/images/Figure10_Nmap_Scan_Execution_Verified.png)

### Task 6: Review Suricata Alerts

![Figure 11 - Review Suricata Alerts](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/09-Suricata-Installation-and-Rule-Configuration-on-PFSense/images/Figure11_Review_Suricata_Alerts.png)

1. Navigated to the `Suricata` service.
2. Went to `Alerts`.
3. Noted the alerts generated by `Suricata`'s `IDS` system as a result of the scan.

![Figure 12 - Alerts Verified](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/09-Suricata-Installation-and-Rule-Configuration-on-PFSense/images/Figure12_Alerts_Verified.png)

