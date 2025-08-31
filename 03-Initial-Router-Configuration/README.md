# Initial Router Configuration in Cisco Packet Tracer

### Project Overview

This lab is designed to practice the initial router configuration in a small network. I set up and connected basic network devices in `Cisco Packet Tracer`. The tasks included connecting a router and switches, assigning IP addresses, and ensuring network connectivity.

### Goals

* Connect a router and switches in `Cisco Packet Tracer`.
* Configure IP addresses and subnet masks on router interfaces.
* Enable router interfaces.
* Save the router configuration.
* Display the router's IP configuration.
* Configure IP addresses, subnet masks, and default gateways on PCs.
* Verify network connectivity between PCs.

### Task Summary

* **Task 1: Connect the Switches to the Router:** Connected the `S1` and `S2` switches to `R1` router. `R1`'s `GigabitEthernet 0/0/0` to `S1`'s `GigabitEthernet 0/1` and `R1`'s `GigabitEthernet 0/0/1` to `S2`'s `GigabitEthernet 0/1`.
* **Task 2: Configure R1's GigabitEthernet 0/0/0 Interface:** Configured `GigabitEthernet 0/0/0` with IP address `192.168.0.1`, subnet mask `255.255.255.0`, and enabled it.
* **Task 3: Configure R1’s GigabitEthernet 0/0/1 Interface:** Configured `GigabitEthernet 0/0/1` with IP address `10.0.0.1`, subnet mask `255.255.255.0`, and enabled it.
* **Task 4: Save and Display Router IP Configuration:** Exited global configuration mode, saved the configurations, and on `R1`'s CLI, in privileged EXEC mode, displayed its IP configuration.
* **Task 5: Configure PC IP Addresses:** Dan and Gil's PCs were configured with IPs `192.168.0.2` and `192.168.0.3`, and a `192.168.0.1` gateway. Jack and Sean's PCs were configured with IPs `10.0.0.2` and `10.0.0.3`, and a `10.0.0.1` gateway. All used a `255.255.255.0` subnet mask.
* **Task 6: Verify Network Connectivity:** Verified connectivity between Dan's and Sean's PCs using the command prompt on Dan's PC.

---

### Step-by-Step

### Task 1: Connect the Switches to the Router

![Figure 1 - Network Topology](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/03-Initial-Router-Configuration/images/Figure01_Network_Topology.png)

1.  Connected `R1`'s `GigabitEthernet 0/0/0` to `S1`'s `GigabitEthernet 0/1`.
2.  Connected `R1`'s `GigabitEthernet 0/0/1` to `S2`'s `GigabitEthernet 0/1`.

![Figure 2 - GigabitEthernet Connections](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/03-Initial-Router-Configuration/images/Figure02_GigabitEthernet_Connections.png)


### Task 2: Configure R1's GigabitEthernet 0/0/0 Interface

![Figure 3 - Configuring Interface Gig 0/0/0](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/03-Initial-Router-Configuration/images/Figure03_Configuring_Interface_Gig_0_0_0.png)

* Connected to the `R1` router's CLI, then typed `enable` followed by `configure terminal` to enter global configuration.
* Entered interface configuration for `GigabitEthernet 0/0/0` using the `interface gigabitethernet 0/0/0` command, then assigned the IP address `192.168.0.1` and subnet mask `255.255.255.0` using the `ip address 192.168.0.1 255.255.255.0` command.
* Enabled the interface by entering `no shutdown` and typed `Exit` to go back to global configuration.

### Task 3: Configure R1’s GigabitEthernet 0/0/1 Interface

![Figure 4 - Configuring Interface Gig 0/0/1](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/03-Initial-Router-Configuration/images/Figure04_Configuring_Interface_Gig_0_0_1.png)

* Entered interface configuration for `GigabitEthernet 0/0/1` and assigned the IP address `10.0.0.1` with subnet mask `255.255.255.0` using the `interface gigabitethernet 0/0/1` and `ip address 10.0.0.1 255.255.255.0` commands.
* Enabled the interface by entering `no shutdown` and typed `Exit` to go back to global configuration.

### Task 4: Save and Display Router IP Configuration

![Figure 5 - Saving Configuration](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/03-Initial-Router-Configuration/images/Figure05_Saving_Configuration.png)

* Exit global configuration mode, saved the configurations with the command `copy running-config startup-config`, in `R1`’s privileged EXEC mode, and verified its IP configuration with the command `show ip interface brief`.

![Figure 6 - Verifying Configuration](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/03-Initial-Router-Configuration/images/Figure06_Verifying_Configuration.png)

### Task 5: Configure PC IP Addresses

![Figure 7 - PC IP Configuration](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/03-Initial-Router-Configuration/images/Figure07_PC_IP_Configuration.png)

* Configured the PC IPs:
    1.  Dan's IP `192.168.0.2` and Gil's IP `192.168.0.3` with gateway `192.168.0.1`.
    2.  Jack's IP `10.0.0.2` and Sean's IP `10.0.0.3` with gateway `10.0.0.1`.
    3.  All with Subnet Mask `255.255.255.0`.

![Figure 8 - PC IP Configuration 2](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/03-Initial-Router-Configuration/images/Figure08_PC_IP_Configuration_2.png)

### Task 6: Verify Network Connectivity

![Figure 9 - Verifying Connectivity](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/03-Initial-Router-Configuration/images/Figure09_Verifying_Connectivity.png)

* From Dan's PC's command prompt verified connectivity to Sean's PC with the command `ping 10.0.0.3`.

![Figure 10 - Verifying Connectivity 2](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/03-Initial-Router-Configuration/images/Figure10_Verifying_Connectivity_2.png)


