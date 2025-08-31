# Implementing Access Control Lists

### Project Overview
This project aims to enhance network security by implementing and verifying `Access Control Lists (ACLs)` on `Cisco` routers. The tasks involve configuring both `standard` and `extended` `ACLs` to filter network traffic based on `source` and `destination IP addresses`, helping control network access as per the defined security policies. I gained hands-on experience in creating, applying, and testing `ACL` rules on `Cisco` devices.

### Goals
* Successfully configure `standard Access Control Lists` on `Cisco` routers to filter traffic based on `source` networks or hosts.
* Successfully configure `extended Access Control Lists` on `Cisco` routers to filter traffic based on `source` and `destination IP addresses`.
* Correctly apply `ACLs` to router interfaces for both `inbound` and `outbound` traffic control.
* Verify the functionality of implemented `ACLs` by testing network connectivity as per the defined rules (successful or failed `pings` as expected).
* Understand the difference between `standard` and `extended` `ACLs` and their appropriate use cases.

### Tasks
* **Task 1**: On `R2`, create a numbered `standard access list` and define rules to deny traffic from the `Marketing network` to the `Server farm`, and permit all other traffic.
* **Task 2**: Apply the `standard ACL` on `R2`'s `GigabitEthernet 0/0` interface for `outbound` traffic, and verify connectivity from `Marketing` and `Management PCs` to `Server1`, expecting the `Marketing PC` `ping` to fail.
* **Task 3**: On `R1`, create a named `standard access list`, define rules to deny traffic from `PC3` and permit all other traffic.
* **Task 4**: Apply this `ACL` to the `GigabitEthernet 0/0` interface for `outbound` traffic. Verify connectivity from `PC3` and `PC4` to `PC1` and `PC2` respectively, expecting the `PC3` to `PC1` connection to fail.
* **Task 5**: On `R2`, create a numbered `extended access list` and define rules to deny traffic from `Marketing PC5` to `R&D PC2` and permit all other traffic.
* **Task 6**: Apply the `extended ACL` on `R2`'s `GigabitEthernet 0/1` interface for `inbound` traffic, and verify connectivity from `R&D PC2` to `Marketing PC5` and `Marketing PC6`, expecting the `R&D PC2` to `Marketing PC5` connection to fail.

### Step-by-Step Guide

---

### Task 1: On R2, create a numbered standard access list and define rules to deny traffic from the Marketing network to the Server farm, and permit all other traffic.

![Figure 1 - R2 ACL Configuration](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/06-Implementing-Access-Control-Lists/images/Figure01_R2_ACL_Configuration.png)

1. Accessed `R2`'s `global configuration mode` and executed the following command: `ip access-list standard 1`.
2. Defined rules to `deny` traffic from the `Marketing network` to the `Server Farm` with the commands: `access-list 1 deny 172.16.2.0 0.0.0.255` and `access-list 1 permit any`.

![Figure 2 - R2 ACL Rules Defined](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/06-Implementing-Access-Control-Lists/images/Figure02_R2_ACL_Rules_Defined.png)

### Task 2: Apply the standard ACL on R2's GigabitEthernet 0/0 interface for outbound traffic, and verify connectivity from Marketing and Management PCs to Server1, expecting the Marketing PC ping to fail.

![Figure 3 - Applying ACL on R2 Interface](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/06-Implementing-Access-Control-Lists/images/Figure03_Applying_ACL_on_R2_Interface.png)

1. In `R2`'s `global configuration mode`, entered `gigabitethernet0/0` settings with the command `interface gigabitethernet0/0` then entered `ip access-group 1 out` to apply the `access list standard 1` for `outbound` traffic.
2. Accessed the `CMD` in `PC3` from the `Management network`, and verified connectivity to the `Server Farm` with the command `ping 172.16.1.1`.
3. Verified the connection from the `Marketing network` to the `Server Farm` by entering the `CMD` in `PC5` and executing `ping 172.16.1.1`. The `ping` failed.

![Figure 4 - R2 Connectivity Test Result](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/06-Implementing-Access-Control-Lists/images/Figure04_R2_Connectivity_Test_Result.png)

### Task 3: On R1, create a named standard access list, define rules to deny traffic from PC3 and permit all other traffic.

![Figure 5 - R1 Named ACL Configuration](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/06-Implementing-Access-Control-Lists/images/Figure05_R1_Named_ACL_Configuration.png)

1. Accessed `R1`'s `global configuration mode` and created a named `ip access list` called `BLOCK_HOST` with the command `ip access-list standard BLOCK_HOST`.
2. Defined the `BLOCK_HOST access list` rules by entering `deny host 192.168.2.1` and `permit any`.

![Figure 6 - R1 Named ACL Rules Defined](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/06-Implementing-Access-Control-Lists/images/Figure06_R1_Named_ACL_Rules_Defined.png)

### Task 4: Apply this ACL to the GigabitEthernet 0/0 interface for outbound traffic. Verify connectivity from PC3 and PC4 to PC1 and PC2 respectively, expecting the PC3 to PC1 connection to fail.

![Figure 7 - Applying ACL on R1 Interface](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/06-Implementing-Access-Control-Lists/images/Figure07_Applying_ACL_on_R1_Interface.png)

1. In `R1`'s `global configuration mode`, entered `gigabitethernet0/0` settings with `interface gigabitethernet0/0`.
2. Applied the `BLOCK_HOST ACL` for `outbound` traffic with `ip access-group BLOCK_HOST out`.
3. Accessed the `CMD` in `PC4` in the `Management`’s network and verified connectivity to `PC2` in `R&D` with `ping 192.168.1.2`.
4. Verified the connectivity from `PC3` in the `Management`’s network to `PC1` in `R&D` with `ping 192.168.1.1`. The `ping` failed.

![Figure 8 - R1 Connectivity Test Result](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/06-Implementing-Access-Control-Lists/images/Figure08_R1_Connectivity_Test_Result.png)

### Task 5: On R2, create a numbered extended access list and define rules to deny traffic from Marketing PC5 to R&D PC2 and permit all other traffic.

![Figure 9 - R2 Extended ACL Configuration](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/06-Implementing-Access-Control-Lists/images/Figure09_R2_Extended_ACL_Configuration.png)

1. Accessed `R2`'s `global configuration mode` and created a numbered `extended access list` by executing `ip access-list extended 100`.
2. Defined the `ACLs` rules and denied traffic from `PC5` in `Marketing` to `PC3` in `R&D` with the command `access-list 100 deny ip host 172.16.2.1 host 192.168.1.2`.
3. Permitted all other traffic with the command `access-list 100 permit ip any any`.

![Figure 10 - R2 Extended ACL Rules Defined](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/06-Implementing-Access-Control-Lists/images/Figure10_R2_Extended_ACL_Rules_Defined.png)

### Task 6: Apply the extended ACL on R2's GigabitEthernet 0/1 interface for inbound traffic, and verify connectivity from R&D PC2 to Marketing PC5 and Marketing PC6, expecting the R&D PC2 to Marketing PC5 connection to fail.

![Figure 11 - Applying Extended ACL on R2 Interface](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/06-Implementing-Access-Control-Lists/images/Figure11_Applying_Extended_ACL_on_R2_Interface.png)

1. In `R2`'s `global configuration mode`, entered `gigabitethernet 0/1` settings with the command `interface gigabitethernet0/1`.
2. Configured the `ACL` for `inbound` traffic with `ip access-group 100 in`.
3. Accessed the `CMD` of `R&D PC2` and executed the following commands: `ping 172.16.2.1` (`Marketing PC5`) and `ping 172.16.2.2` (`Marketing PC6`). The `ping` to `PC5` failed.

![Figure 12 - Final Connectivity Test Result](https://raw.githubusercontent.com/iagsalazar1-cs/Network-Administration-and-Labs/main/06-Implementing-Access-Control-Lists/images/Figure12_Final_Connectivity_Test_Result.png)
