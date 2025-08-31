# PfSense Firewall Rule Configuration

### Project Overview
This lab offers practical `firewall` management skills in a simulated network environment. It utilizes hands-on tasks across various `virtual machines` and operating systems to build an understanding of `firewall` rule configuration. This includes applying rules to control network traffic, specifically `ICMP` (`ping`), through the `pfSense web interface`.

### Goals
* Efficiently navigate between `virtual machines` (`Windows Client`, `Windows Server`) and establish `VPN connections` on the client.
* Utilize the `ping` command to test network connectivity and observe `firewall rule` effects.
* Access and navigate the `pfSense web interface`, specifically to the `"Firewall > Rules"` section.
* Create and configure new `firewall rules` by modifying parameters such as `Action`, `Protocol`, `Interface`, and `Address Family`.
* Understand and apply `firewall rule` order using `drag & drop` functionality.

### Task Summary
* **Task 1:** Initial `VPN` Connection & Connectivity Test: Established `Windows Client` network connectivity via `VPN` setup and verified reachability with a `ping` test to `192.168.10.1`.
* **Task 2:** Accessing `PfSense` & Initiating Rule Creation: Gained administrative access to the `pfSense web interface` from the `Windows Server` and prepared to define a new `firewall rule`.
* **Task 3:** Blocking `ICMP` & Testing: Implemented a `pfSense firewall rule` to block `ICMP` traffic, with `Windows Client` connectivity re-tested to confirm `pings` were no longer successful.
* **Task 4:** Allowing `ICMP` with New Rule & Testing: Added a `pfSense rule` to permit `ICMP` traffic, overriding the existing block rule, and re-verified network connectivity with successful `pings` observed.
* **Task 5:** Re-ordering Rules & Final Connectivity Test: Reverted `pfSense` rules, prioritizing the block over the allow, and a final `Windows Client ping` test confirmed blocked connectivity.

### Step-by-Step Guide

---

### Task 1: Initial `VPN` Connection & Connectivity Test (`Windows Client`)

![Figure 1 - Initial VPN Connection & Connectivity Test](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/08-PFSense-Firewall-Rule-Configuration/images/Figure01_Initial_VPN_Connection_Test.png)

1. Navigated to the `Windows Client` machine.
2. Connected to the `VPN` via desktop shortcut.
3. `Pinged` `192.168.10.1` to confirm reachability to the `pfsense firewall` in the lab environment.

![Figure 2 - Initial VPN Connection & Connectivity Test Verified](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/08-PFSense-Firewall-Rule-Configuration/images/Figure02_Initial_VPN_Connection_Test_Verified.png)

### Task 2: Accessing `PfSense` & Initiating Rule Creation (`Windows Server`)

![Figure 3 - Accessing PfSense & Initiating Rule Creation](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/08-PFSense-Firewall-Rule-Configuration/images/Figure03_Accessing_PfSense_Initiating_Rule_Creation.png)

1. Returned to the `Windows Server`.
2. Accessed `pfSense web interface` via desktop link.
3. Logged in with `admin` / `pfsense`, ignoring insecure connection warnings.
4. Navigated to `"Firewall > Rules"` and initiated new rule addition on the `"L2TP VPN"` tab.

![Figure 4 - Accessing PfSense & Initiating Rule Creation Verified](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/08-PFSense-Firewall-Rule-Configuration/images/Figure04_Accessing_PfSense_Initiating_Rule_Creation_Verified.png)

### Task 3: Blocking `ICMP` & Testing (`PfSense` & `Windows Client`)

![Figure 5 - Blocking ICMP & Testing](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/08-PFSense-Firewall-Rule-Configuration/images/Figure05_Blocking_ICMP_Testing.png)

1. Configured rule to block `ICMP`: `Action` `"Block,"` `Protocol` `"ICMP."`
2. Saved and applied changes; verified rule visibility.
3. Returned to `Windows Client`.
4. `Pinged` `192.168.10.1`; confirmed `pings` were blocked.

![Figure 6 - Blocking ICMP & Testing Verified](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/08-PFSense-Firewall-Rule-Configuration/images/Figure06_Blocking_ICMP_Testing_Verified.png)

### Task 4: Allowing `ICMP` with New Rule & Testing (`PfSense` & `Windows Client`)

![Figure 7 - Allowing ICMP with New Rule & Testing](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/08-PFSense-Firewall-Rule-Configuration/images/Figure07_Allowing_ICMP_with_New_Rule_Testing.png)

1. Returned to `Windows Server`, accessed `pfSense`.
2. Created new rule to `pass ICMP`: `Action` `"Pass,"` `Interface` `"L2TP VPN,"` `Address Family` `"IPv4,"` `Protocol` `"ICMP."`
3. Dragged this new `"pass"` rule above the `"block"` rule; saved and applied changes (reload occurred).
4. Returned to `Windows Client` and `pinged` `192.168.10.1`; confirmed `pings` were successful due to priority.

![Figure 8 - Allowing ICMP with New Rule & Testing Verified](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/08-PFSense-Firewall-Rule-Configuration/images/Figure08_Allowing_ICMP_with_New_Rule_Testing_Verified.png)

### Task 5: Re-ordering Rules & Final Connectivity Test (`PfSense` & `Windows Client`)

![Figure 9 - Re-ordering Rules & Final Connectivity Test](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/08-PFSense-Firewall-Rule-Configuration/images/Figure09_Re-ordering_Rules_Final_Connectivity_Test.png)

1. Returned to `Windows Server`, accessed `pfSense`.
2. Used `drag & drop` to place `"block"` rule above `"allow"` rule; saved and applied (reload occurred).
3. Returned to `Windows Client` and `pinged` `192.168.10.1` one final time.
4. Confirmed `pings` were blocked again due to rule precedence.

![Figure 10 - Re-ordering Rules & Final Connectivity Test Verified](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/08-PFSense-Firewall-Rule-Configuration/images/Figure10_Re-ordering_Rules_Final_Connectivity_Test_Verified.png)
