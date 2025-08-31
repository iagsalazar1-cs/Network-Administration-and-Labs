# Configuring Static Routes on a Cisco Router

### Project Overview

This project is focused on configuring `IPv4` `static routes` on `Cisco` routers. The lab involves configuring `static routes` between three different `LANs` and an external network. The project will cover how to establish network connectivity by manually configuring `routing tables`.

### Goals

* Understand the principles of static routing.
* Gain hands-on experience with `Cisco IOS` commands for configuring static routes.
* Configure `IPv4` static routes to enable communication between different `LANs`.
* Learn to verify static route configurations and troubleshoot connectivity issues.
* Develop skills in network configuration and troubleshooting.

### Task Summary

* **Task 1: Initial Connectivity Test and Analysis**: Open PC1's command prompt (`CMD`), test connectivity to PC2 using the `ping` command, and investigate the connectivity failure by inspecting R1's routing table.
* **Task 2: R1 Static Route Configuration**: On router R1, access the global configuration mode, configure static routes for the following networks, using the `serial 0/0/0` interface: `192.168.0.64/26`, `192.168.0.128/26`, `192.168.0.196/30`, and exclude the `210.10.10.0` network from static route configuration.
* **Task 3: R2 Next-Hop Static Route Configuration**: On router R2, access the global configuration mode, configure next-hop static routes for the following networks: `192.168.0.0/26`, with the next hop IP address as `192.168.0.193`, `192.168.0.128/26`, with the next hop IP address as `192.168.0.198`, and exclude the `210.10.10.0` network.
* **Task 4: R3 Static Route Configuration**: On router R3, access the global configuration mode, configure static routes for the following networks, using the `serial 0/0/1` interface: `192.168.0.0/26`, `192.168.0.64/26`, `192.168.0.192/30`, and exclude the `210.10.10.0` network.
* **Task 5: Routing Table Verification**: Display the routing table of each router (R1, R2, and R3), and verify that the static routes configured in the previous tasks are present and correct.
* **Task 6: Connectivity Verification**: Verify connectivity from PC1 to PC2 using the `ping` command.
* **Task 7: Path Determination**: Determine the path that network traffic takes between PC1 and PC2 (using `traceroute` or a similar tool).

### Step-by-Step Guide

---

### Task 1: Initial Connectivity Test and Analysis

![Figure 1 - Initial Connectivity Test and Analysis](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/04-Configuring-Static-Routes/images/Figure01_Initial_Connectivity_Test.png)

1. Accessed the `CMD` window of PC1 and executed the following command: `ping 192.168.0.66`.
2. Accessed the R1 router with user `EXEC` privileges via the `CLI` tab and executed the following command: `show ip route`.
3. Determined R1’s network `192.168.0.0/26` is directly connected via `GigabitEthernet0/0` and `192.168.0.192/30` is directly connected via `Serial0/0/0`. Verified network static routes have not been configured.

![Figure 2 - Connectivity Analysis and Routing Table](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/04-Configuring-Static-Routes/images/Figure02_Connectivity_Analysis.png)

### Task 2: R1 Static Route Configuration

![Figure 3 - R1 Static Route Configuration](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/04-Configuring-Static-Routes/images/Figure03_R1_Static_Route_Configuration.png)

1. Configured these routes on R1 to enable it to forward traffic to the networks connected to R2 and R3. Accessed R1’s configuration mode and executed the following commands:
    a. `ip route 192.168.0.64 255.255.255.192 serial 0/0/0`
    b. `ip route 192.168.0.128 255.255.255.192 serial 0/0/0`
    c. `ip route 192.168.0.196 255.255.255.252 serial 0/0/0`

![Figure 4 - R1 Routes Added](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/04-Configuring-Static-Routes/images/Figure04_R1_Routes_Added.png)

### Task 3: R2 Next-Hop Static Route Configuration

![Figure 5 - R2 Next-Hop Static Route Configuration](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/04-Configuring-Static-Routes/images/Figure05_R2_Next_Hop_Static_Route_Configuration.png)

1. Configured routes on R2 to enable it to forward traffic to the networks connected to R1 and R3. Accessed R2’s configuration mode and executed the following commands:
    a. `ip route 192.168.0.0 255.255.255.192 192.168.0.193`
    b. `ip route 192.168.0.128 255.255.255.192 192.168.0.198`

![Figure 6 - R2 Routes Added](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/04-Configuring-Static-Routes/images/Figure06_R2_Routes_Added.png)

### Task 4: R3 Static Route Configuration

![Figure 7 - R3 Static Route Configuration](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/04-Configuring-Static-Routes/images/Figure07_R3_Static_Route_Configuration.png)

1. Configured routes on R3 to enable it to forward traffic to the networks connected to R1 and R2. Accessed the R3’s configuration mode and executed the following commands:
    a. `ip route 192.168.0.0 255.255.255.192 serial 0/0/1`
    b. `ip route 192.168.0.64 255.255.255.192 serial 0/0/1`
    c. `ip route 192.168.0.192 255.255.255.252 serial 0/0/1`

![Figure 8 - R3 Routes Added](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/04-Configuring-Static-Routes/images/Figure08_R3_Routes_Added.png)

### Task 5: Routing Table Verification

![Figure 9 - Routing Table Verification](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/04-Configuring-Static-Routes/images/Figure09_Routing_Table_Verification.png)

1. Displayed the routing table of each router (R1, R2, and R3), and verified that the static routes configured in the previous tasks are present and correct. Accessed the terminal window of each router, and executed the following command: `show ip route`.

![Figure 10 - Verified Routing Tables](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/04-Configuring-Static-Routes/images/Figure10_Verified_Routing_Tables.png)

### Task 6: Connectivity Verification

![Figure 11 - Connectivity Verification](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/04-Configuring-Static-Routes/images/Figure11_Connectivity_Verification.png)

1. Accessed the `CMD` window of PC1 and executed the following command: `ping 192.168.0.66`. The connection was successful.

![Figure 12 - Successful Ping](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/04-Configuring-Static-Routes/images/Figure12_Successful_Ping.png)

### Task 7: Path Determination

![Figure 13 - Path Determination](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/04-Configuring-Static-Routes/images/Figure13_Path_Determination.png)

1. From the `CMD` window of PC1 and executed the following command: `tracert 192.168.0.66`. Verified the route of the ping request to PC2 starting with the first hop to `192.168.0.1` in R1, to the next hop at `192.168.0.194` in R2, ending at PC2’s `192.168.0.66`.

![Figure 14 - Traceroute Results](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/04-Configuring-Static-Routes/images/Figure14_Traceroute_Results.png)
