# Configuring VLANs and Trunks

### Project Overview
This project involves the configuration of `Virtual Local Area Networks (VLANs)` and `trunking` on `Cisco` switches. The primary goal is to segment the network to improve performance, enhance security, and facilitate network management. The project includes configuring `VLANs` on multiple switches, assigning switch ports to specific `VLANs`, establishing `trunk links` between switches to carry `VLAN` traffic, and verifying network connectivity.

### Goals
* Create `VLANs` to segment network traffic.
* Configure switch ports to support specific `VLANs`.
* Establish `trunk links` between switches to propagate `VLAN` information.
* Verify network connectivity between devices in the same `VLAN`.
* Isolate network traffic for workstations and servers.
* Implement a native `VLAN` for untagged traffic.

### Task Summary
* **Task 1: Display VLANs**: Access the `CLI` of each switch and display all configured `VLANs` using the `show vlan brief` command.
* **Task 2: Name VLANs**: Access the global configuration mode of each switch and name `VLAN 10` as "`Workstation`" and `VLAN 20` as "`Servers`".
* **Task 3: Configure S1 for VLAN Access**: Access the global configuration mode of `S1`, configure `FastEthernet` ports `0/1` and `0/2` for `VLAN 10`, and configure `FastEthernet` port `0/3` for `VLAN 20`.
* **Task 4: Configure S2 for VLAN Access**: Access the global configuration mode of `S2`, configure `FastEthernet` ports `0/1` through `0/4` for `VLAN 10`, and configure `FastEthernet` ports `0/5` and `0/6` for `VLAN 20`.
* **Task 5: Initial Connectivity Test**: Open the command prompt on `PC1` and test connectivity to `PC6` using the `ping` command, noting the expected failure.
* **Task 6: Configure Trunking on S1 and S2**: Access the global configuration mode of `S1` and configure `GigabitEthernet` ports `0/1` and `0/2` as `trunk ports`, and on `S2`, configure `GigabitEthernet` port `0/1` as a `trunk port`.
* **Task 7: Create Native VLAN**: Access the global configuration mode on `S1` and `S2`, and create `VLAN 30` and name it "`Native`" on both switches.
* **Task 8: Configure Native VLAN on Trunks**: On `S1` and `S2`, configure `GigabitEthernet` port `0/1` as a `trunk`, with `VLAN 30` as the native `VLAN`, and then save the configurations.
* **Task 9: Final Connectivity Test**: Open the command prompt on `PC1` and test connectivity to `PC3` using the `ping` command.

### Step-by-Step Guide

---

### Task 1: Display VLANs

![Figure 1 - Display VLANs](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure01_Display_VLANs.png)

1. Accessed the `CLI` interface of the `S1` switch and executed the following commands: `enable` and `show vlan brief`.
2. Accessed the `CLI` interface of the `S2` switch and executed the following commands: `enable` and `show vlan brief`.

![Figure 2 - VLAN Brief Output](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure02_VLAN_Brief_Output.png)

### Task 2: Name VLANs

![Figure 3 - Naming VLANs](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure03_Naming_VLANs.png)

1. Accessed `S1’s` global configuration mode and executed the following commands:
    a. `vlan 10`
    b. `name Workstation`
    c. `exit`
    d. `vlan 20`
    e. `name Servers`
    f. `exit`
2. Accessed `S2’s` global configuration mode and executed the following commands:
    a. `vlan 10`
    b. `name Workstation`
    c. `Exit`
    d. `vlan 20`
    e. `name Servers`
    f. `exit`

![Figure 4 - VLANs Named](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure04_VLANs_Named.png)

### Task 3: Configure S1 for VLAN Access

![Figure 5 - Configuring S1 for VLAN Access](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure05_Configuring_S1_Access.png)

1. Accessed `S1’s` global configuration mode and executed the following commands:
    a. `interface range fastethernet 0/1-2`
    b. `switchport mode access`
    c. `switchport access vlan 10`
    d. `Exit`
    e. `interface fastethernet 0/3`
    f. `switchport mode access`
    g. `switchport access vlan 20`
    h. `Exit`

![Figure 6 - S1 Access Configuration](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure06_S1_Access_Configuration.png)

### Task 4: Configure S2 for VLAN Access

![Figure 7 - Configuring S2 for VLAN Access](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure07_Configuring_S2_Access.png)

1. Accessed `S2’s` global configuration mode and executed the following commands:
    a. `interface range fastethernet 0/1-4`
    b. `switchport mode access`
    c. `switchport access vlan 10`
    d. `Exit`
    e. `interface range fastethernet 0/5-6`
    f. `switchport mode access`
    g. `switchport access vlan 20`
    h. `exit`

![Figure 8 - S2 Access Configuration](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure08_S2_Access_Configuration.png)

### Task 5: Initial Connectivity Test

![Figure 9 - Initial Connectivity Test](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure09_Initial_Connectivity_Test.png)

1. Accessed the `CMD` window of `PC1` and executed the following command: `ping 10.0.0.6`.

![Figure 10 - Ping Failure](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure10_Ping_Failure.png)

### Task 6: Configure Trunking on S1 and S2

![Figure 11 - Configuring Trunking](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure11_Configuring_Trunks.png)

1. Accessed `S1’s` global configuration mode and executed the following commands:
    a. `interface range gigabitethernet 0/1-2`
    b. `switchport mode trunk`
    c. `exit`
2. Accessed `S2’s` global configuration mode and executed the following commands:
    a. `Interface gigabitethernet 0/1`
    b. `switchport mode trunk`
    c. `exit`

![Figure 12 - Trunk Ports Configured](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure12_Trunk_Ports_Configured.png)

### Task 7: Create Native VLAN

![Figure 13 - Creating Native VLAN](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure13_Creating_Native_VLAN.png)

1. Accessed `S1’s` global configuration mode and executed the following commands:
    a. `vlan 30`
    b. `name Native`
    c. `exit`
2. Accessed `S2’s` global configuration mode and executed the following commands:
    a. `vlan 30`
    b. `name Native`
    c. `exit`

![Figure 14 - Native VLAN Created](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure14_Native_VLAN_Created.png)

### Task 8: Configure Native VLAN on Trunks

![Figure 15 - Configuring Native VLAN on Trunks](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure15_Configuring_Native_VLAN_on_Trunks.png)

1. Access `S1’s` global configuration mode and execute the following commands:
    a. `interface gigabitethernet 0/1`
    b. `switchport trunk native vlan 30`
    c. `End`
    d. `copy running-config startup-config`
2. Access `S2’s` global configuration mode and execute the following commands:
    a. `interface gigabitethernet 0/1`
    b. `switchport trunk native vlan 30`
    c. `End`
    d. `copy running-config startup-config`

![Figure 16 - Native VLAN Configured on Trunks](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure16_Native_VLAN_Configured_on_Trunks.png)

### Task 9: Final Connectivity Test

![Figure 17 - Final Connectivity Test](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure17_Final_Connectivity_Test.png)

1. Access the `CMD` window of `PC1` and execute the following command: `ping 10.0.0.3`. The ping was successful.

![Figure 18 - Successful Ping](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/05-Configuring-VLANs-and-Trunks/images/Figure18_Successful_Ping.png)
