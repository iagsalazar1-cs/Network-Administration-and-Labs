# Network Address Translation Configurations (NAT)

### Project Overview
This lab focuses on configuring and verifying `Network Address Translation (NAT)` on `Cisco` routers. The project covers three essential types of `NAT`: `Static NAT`, `Dynamic NAT`, and `NAT Overload (PAT)` to provide hands-on experience with each type. The lab includes configuration of each `NAT` type on designated routers, test network connectivity, and analyze network behavior to confirm correct `NAT` operation. `NAT` is a crucial technology for `IP address` management in scenarios where private networks need to communicate with external networks like the `internet` using a single `IP address`.

### Goals
* Understand the fundamental concepts of `NAT` and its role in network communication.
* Gain practical experience in configuring `Static NAT`, `Dynamic NAT`, and `NAT Overload (PAT)` on `Cisco` routers.
* Develop skills in verifying `NAT` configurations and troubleshooting connectivity issues.
* Analyze network behavior to observe how `NAT` translates `IP addresses`.
* Become proficient in using `Cisco IOS` commands related to `NAT` configuration and verification.

### Tasks
* **Task 1**: `Static NAT` Configuration - Configure `Static NAT` on router `R1-Static`; Translate `PC1`'s internal `IP address` (`192.168.1.20`) to the external `IP address` (`80.80.80.1`).
* **Task 2**: `Static NAT` Verification - Verify the `Static NAT` configuration; `Ping` the remote server (`200.200.200.200`) from `PC1-Static`; Inspect the `ping` packet at the `R1-Static` router (`80.80.80.1`) to confirm the `source IP address translation`; Use the `show ip nat translations` and `show ip nat statistics` commands on `R1-Static`.
* **Task 3**: `Dynamic NAT` Configuration - Configure `Dynamic NAT` on router `R1-Dynamic`; Translate the internal network range (`192.168.1.0/24`) to a pool of external `IP addresses` (`80.80.80.5` - `80.80.80.9`).
* **Task 4**: `Dynamic NAT` Verification - Verify the `Dynamic NAT` configuration; `Ping` the remote server (`200.200.200.200`) from `PC1-Dynamic`, `PC2-Dynamic`, and `PC3-Dynamic`; Inspect the `ping` packets at the `R1-Dynamic` router to verify that each `PC` uses a different external `IP address` from the pool.
* **Task 5**: `NAT Overload (PAT)` Configuration - Configure `NAT Overload (PAT)` on router `R1-PAT`; Allow multiple internal devices to share a single external `IP address` (`80.80.80.1`) using different `port numbers`.
* **Task 6**: `NAT Overload (PAT)` Verification - Verify the `NAT Overload (PAT)` configuration; `Ping` the remote server (`200.200.200.200`) from `PC1-PAT`, `PC2-PAT`, and `PC3-PAT`; Inspect the `ping` packets at the `R1-PAT` router (`80.80.80.1`) to ensure all `PCs` share the same external `IP address` but use different `source port numbers`.

### Step-by-Step Guide

---

### Task 1: Static NAT Configuration - Configure Static NAT on router R1-Static; Translate PC1's internal IP address (192.168.1.20) to the external IP address (80.80.80.1).

![Figure 1 - Static NAT Configuration](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/07-Configuring-Static-Dynamic-Overload-NAT/images/Figure01_Static_NAT_Configuration.png)

* Accessed `R1-Static`'s `CLI` and executed the following commands to configure `Static NAT`, mapping the internal `IP address 192.168.1.20` to the public `IP address 80.80.80.1`:
1. `enable`
2. `configure terminal`
3. `interface gigabitEthernet 0/0`
4. `ip nat inside`
5. `Exit`
6. `interface serial 0/0/0`
7. `ip nat outside`
8. `Exit`
9. `ip nat inside source static 192.168.1.20 80.80.80.1`
10. `End`
11. `copy running-config startup-config`

![Figure 2 - Static NAT Commands](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/07-Configuring-Static-Dynamic-Overload-NAT/images/Figure02_Static_NAT_Commands.png)

### Task 2: Static NAT Verification - Verify the Static NAT configuration; Ping the remote server from PC1-Static; Inspect the ping packet at the R1-Static router to confirm the source IP address translation; Use the show ip nat translations and show ip nat statistics commands on R1-Static.

![Figure 3 - Static NAT Verification](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/07-Configuring-Static-Dynamic-Overload-NAT/images/Figure03_Static_NAT_Verification.png)

1. Accessed `PC1-Static`'s command prompt and executed the command `ping 200.200.200.200` to verify the connectivity and checked the `NAT` translation.
2. On `R1-Static`, entered the command `show ip nat translations` to confirm that the internal `IP` (`192.168.1.20`) is being translated to the global `IP` (`80.80.80.1`) and checked the `ICMP` connections.
3. Checked `NAT` statistics using the command `show ip nat statistics`. Verified the `Total translations` and ensured that `Static NAT` has been configured properly.

![Figure 4 - Static NAT Verified](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/07-Configuring-Static-Dynamic-Overload-NAT/images/Figure04_Static_NAT_Verified.png)

### Task 3: Dynamic NAT Configuration - Configure Dynamic NAT on router R1-Dynamic; Translate the internal network range (192.168.1.0/24) to a pool of external IP addresses (80.80.80.5 - 80.80.80.9).

![Figure 5 - Dynamic NAT Configuration](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/07-Configuring-Static-Dynamic-Overload-NAT/images/Figure05_Dynamic_NAT_Configuration.png)

* Accessed `R1-Dynamic`'s `CLI` and executed the following commands to configure `Dynamic NAT`, translating the internal `IP` range (`192.168.1.0/24`) to a pool of external `IP addresses` (`80.80.80.5` - `80.80.80.9`):
1. `enable`
2. `configure terminal`
3. `interface gigabitEthernet 0/0`
4. `ip nat inside`
5. `exit`
6. `interface serial 0/0/0`
7. `ip nat outside`
8. `exit`
9. `access-list 1 permit 192.168.1.0 0.0.0.255`
10. `ip nat pool mypool 80.80.80.5 80.80.80.9 netmask 255.0.0.0`
11. `ip nat inside source list 1 pool mypool`
12. `end`
13. `copy running-config startup-config`

![Figure 6 - Dynamic NAT Commands](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/07-Configuring-Static-Dynamic-Overload-NAT/images/Figure06_Dynamic_NAT_Commands.png)

### Task 4: Dynamic NAT Verification - Verify the Dynamic NAT configuration; Ping the remote server from PC1-Dynamic, PC2-Dynamic, and PC3-Dynamic; Inspect the ping packets at the R1-Dynamic router to verify that each PC uses a different external IP address from the pool.

![Figure 7 - Dynamic NAT Verification](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/07-Configuring-Static-Dynamic-Overload-NAT/images/Figure07_Dynamic_NAT_Verification.png)

1. Accessed the command prompt of `PC1-Dynamic`, `PC2-Dynamic`, and `PC3-Dynamic`, and executed `ping 200.200.200.200` to verify connectivity.
2. On `R1-Dynamic`, used the command `show ip nat translations` to inspect the packet and verified that the internal `IPs` (`192.168.1.20`, `192.168.1.21`, `192.168.1.22`) are translated to different global `IPs` from the pool.
3. Checked `NAT` statistics using the command `show ip nat statistics`. Verified the `Total translations` and ensured that `Dynamic NAT` is functioning correctly.

![Figure 8 - Dynamic NAT Verified](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/07-Configuring-Static-Dynamic-Overload-NAT/images/Figure08_Dynamic_NAT_Verified.png)

### Task 5: NAT Overload (PAT) Configuration - Configure NAT Overload (PAT) on router R1-PAT; Allow multiple internal devices to share a single external IP address (80.80.80.1) using different port numbers.

![Figure 9 - PAT Configuration](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/07-Configuring-Static-Dynamic-Overload-NAT/images/Figure09_PAT_Configuration.png)

* Accessed `R1-PAT`'s `CLI` and execute the following commands to configure `NAT Overload (PAT)`, which allows multiple internal devices to share a single public `IP` (`80.80.80.1`) by using `port` differentiation:
1. `enable`
2. `configure terminal`
3. `interface gigabitEthernet 0/0`
4. `ip nat inside`
5. `exit`
6. `interface serial 0/0/0`
7. `ip nat outside`
8. `exit`
9. `access-list 1 permit 192.168.1.0 0.0.0.255`
10. `ip nat inside source list 1 interface serial 0/0/0 overload`
11. `end`
12. `copy running-config startup-config`

![Figure 10 - PAT Commands](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/07-Configuring-Static-Dynamic-Overload-NAT/images/Figure10_PAT_Commands.png)

### Task 6: NAT Overload (PAT) Verification - Verify the NAT Overload (PAT) configuration; Ping the remote server from PC1-PAT, PC2-PAT, and PC3-PAT; Inspect the ping packets at the R1-PAT router to ensure all PCs share the same external IP address but use different source port numbers.

![Figure 11 - PAT Verification](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/07-Configuring-Static-Dynamic-Overload-NAT/images/Figure11_PAT_Verification.png)

1. Accessed the command prompt of `PC1-PAT`, `PC2-PAT`, and `PC3-PAT`, and executed the command `ping 200.200.200.200` to verify connectivity.
2. On `R1-PAT`, used the command `show ip nat translations` to inspect the packets and verified that the internal `IPs` (`192.168.1.20`, `192.168.1.21`, `192.168.1.22`) are sharing the same global `IP` (`80.80.80.1`) with different `ports`.
3. Checked `NAT` statistics using the command `show ip nat statistics`. Verified the `Total translations` and ensured that `NAT Overload (PAT)` works properly.

![Figure 12 - PAT Verified](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/07-Configuring-Static-Dynamic-Overload-NAT/images/Figure12_PAT_Verified.png)
