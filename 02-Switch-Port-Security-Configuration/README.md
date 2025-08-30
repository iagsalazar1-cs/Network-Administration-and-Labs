# Configuration and Verification of Switch Port Security

## Project Overview

Configured port security on a `Cisco switch` using `Cisco Packet Tracer`. The objective is to populate the `MAC address table`, apply port security policies, and test the system for violations to ensure secure network functionality.

## Goals

* Populate and display the `S1` switch's `MAC address table`. Enable port security on `FastEthernet 0/1`, `0/2`, and `0/3`.

* Set authorized `MAC addresses` for `FastEthernet 0/1`, `0/2` and `FastEthernet 0/3` (`sticky`).

* Set the violation mode for `FastEthernet 0/1` to `shutdown`, `FastEthernet 0/2` to `restrict`, and `FastEthernet 0/3` to `protect`.

* Save the `S1` switch configuration and disable unused ports on `S1`.

* Verify port security settings and test port security violations.

* Verify `FastEthernet 0/1` is in `err-disabled` state and re-enable it.

* Verify interface recovery.

## Task Summary

* **Task 1: Populate and Display the MAC Address Table**: Populate the `S1` switch's `MAC address table` using `pings` and display it.

* **Task 2: Enable Port Security and Configure Authorized MAC Addresses on FastEthernet 0/1-3**: Enable port security on `FastEthernet 0/1`, `0/2`, and `0/3`. Set the authorized `MAC addresses` for `FastEthernet 0/1` and `FastEthernet 0/2` to be fixed. Set `FastEthernet 0/3`'s authorized `MAC address` to `sticky`.

* **Task 3: Configure Violation Modes on FastEthernet 0/1, 0/2, and 0/3**: Set the violation mode for `FastEthernet 0/1` to `shutdown`, `FastEthernet 0/2` to `restrict`, and `FastEthernet 0/3` to `protect`.

* **Task 4: Disable Unused Ports and Save Switch Configuration**: Disable unused ports on the `S1` switch and save the configuration.

* **Task 5: Verify Port Security Settings and Test Port Security Violation**: Verify port security settings and test for violations.

* **Task 6: Verify Err-Disabled State and Recover from Err-Disabled State**: Verify `FastEthernet 0/1` is in `err-disabled` state and re-enable it.

* **Task 7: Verify Interface Recovery**: Verify that the interface returned to its normal state by performing a connectivity test from `Mike's PC` to `Joey's PC`.

## Tasks

### Task 1: Populate and Display the MAC Address Table

![Figure 1 - Accessed the Command Prompt of Mike’s PC](https://github.com/placeholder.png)

* Accessed the Command Prompt of Mike’s PC and executed the following commands: `ping 10.0.0.2`, `ping 10.0.0.3`, `ping 10.0.0.4`.

* Then performed the same step in Joey’s PC and pinged Mike’s PC with `ping 10.0.0.1`.

* Executed `show mac-address-table` in the switch's CLI to display the populated MAC Address Table.

![Figure 2 - Executed show mac-address-table](https://github.com/placeholder.png)

### Task 2: Enable Port Security and Configure Authorized MAC Addresses on FastEthernet 0/1-3

![Figure 3 - Entered privileged EXEC mode](https://github.com/placeholder.png)

* Entered privileged EXEC mode, then global configuration with `enable` and `configure terminal`.

* Entered `interface range fastethernet 0/1-3` and set `switchport mode access` and enabled port security with `switchport port-security`.

* Entered the settings of both `interface fastethernet 0/1` and `interface fastethernet 0/2` and set the authorized MAC Address to be fixed with the command `switchport port-security mac-address <mac-address>`.

* Entered the `interface fastethernet 0/3` settings and configured its MAC Address to be sticky with the command `switchport port-security mac-address sticky`.

![Figure 4 - configured its MAC Address to be sticky](https://github.com/placeholder.png)

### Task 3: Configure Violation Modes on FastEthernet 0/1, 0/2, and 0/3

![Figure 5 - Entered the settings of interface fastethernet 0/1](https://github.com/placeholder.png)

* Entered the settings of `interface fastethernet 0/1` and configured the violation mode to Shutdown with the commands: `Interface fastethernet 0/1` and `switchport port-security violation shutdown`.

* Entered the settings of `interface fastethernet 0/2` and configured the violation mode to Restrict with the commands: `Interface fastethernet 0/2` and `switchport port-security violation restrict`.

* Entered the settings of `interface fastethernet 0/3` and configured the violation mode to Protect with the commands: `Interface fastethernet 0/3` and `switchport port-security violation protect`.

![Figure 6 - configured the violation mode to Protect](https://github.com/placeholder.png)

### Task 4: Disable Unused Ports and Save Switch Configuration

![Figure 7 - Disabled the remaining fast ethernet interfaces](https://github.com/placeholder.png)

* Disabled the remaining fast ethernet interfaces by entering the range settings with the commands: `interface range fastethernet 0/5-24` and `shutdown`.

* Then disabled the `interface range gigabitethernet 0/1-2` by entering `interface range gigabitethernet 0/1-2` and `shutdown`.

* Exited global configuration mode and saved the current configuration using the command `copy running-config startup-config`.

![Figure 8 - saved the current configuration](https://github.com/placeholder.png)

### Task 5: Verify Port Security Settings and Test Port Security Violation

![Figure 9 - Verified port security by displaying the current violation modes](https://github.com/placeholder.png)

* Verified port security by displaying the current violation modes with the command `show-port-security`.

* Disconnected Mike’s PC from the S1 switch and connected the rogue laptop on the `fastethernet 0/1` port of the switch.

* Then executed `ping 10.0.0.3`. The ping failed since the MAC Address was fixed previously.

![Figure 10 - The ping failed since the MAC Address was fixed previously](https://github.com/placeholder.png)

### Task 6: Verify Err-Disabled State and Recover from Err-Disabled State

![Figure 11 - Reconnected Mike’s PC back to the switch](https://github.com/placeholder.png)

* Reconnected Mike’s PC back to the switch.

* In the switch’s cli executed the command `show interface fastethernet 0/1` to verify the Err-Disabled state.

* Entered `interface fastethernet 0/1` settings with `interface fastethernet 0/1` and re-enabled the interface with the commands `shutdown` and `no shutdown`.

![Figure 12 - re-enabled the interface](https://github.com/placeholder.png)

### Task 7: Verify Interface Recovery

![Figure 13 - Performed a connectivity test from Mike's PC to Joey's PC](https://github.com/placeholder.png)

* Performed a connectivity test from Mike's PC to Joey's PC for interface normal state verification:

* Verified connectivity from Mike’s PC to Joey’s PC with the command `ping 10.0.0.2`. The connection was successful.

![Figure 14 - The connection was successful](https://github.com/placeholder.png)
