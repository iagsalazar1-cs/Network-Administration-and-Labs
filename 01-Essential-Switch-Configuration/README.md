# Essential Switch Configuration in Packet Tracer

### Overview

This project focuses on configuring and verifying switch and PC settings within **Cisco Packet Tracer** to establish basic network connectivity. The tasks involve setting up communication between endpoints, configuring network security settings, and testing connectivity. The network for this project consists of a Local Area Network (LAN) with a switch (`S1-Floor1`) connecting two PCs: `John's PC` and `Micky's PC`. An `Admin PC` is also present, used for configuration but not directly connected to the switch's network ports.

### Goals

1. Connect to a **Cisco switch** using the console port.

2. Navigate the **Cisco IOS CLI**, including user `EXEC` mode, privileged `EXEC` mode, and global configuration mode.

3. Configure basic switch settings, including the hostname, system time, user accounts, and passwords.

4. Secure switch access by configuring console authentication and encrypting passwords.

5. Configure `IP addresses` on PCs and verify network connectivity between them.

6. Display and interpret switch interface information.

7. Examine the switch's `MAC` address table and save switch configurations.

### Project Tasks

* **Task 1:** Connect to the Switch, Explore `CLI` Modes, and Set System Time: Connect `Admin PC` to switch console, explore user `EXEC` mode, enter privileged `EXEC`, set switch time.

* **Task 2:** Enter Global Configuration Mode, Set Hostname, and Configure User and Privileged `EXEC` Passwords: Enter global configuration, set hostname, configure user and privileged `EXEC` passwords.

* **Task 3:** Configure Switch Security: set `MOTD` banner, configure console authentication.

* **Task 4:** Encrypt and Save Configurations: Exit console configuration, encrypt passwords, save configurations.

* **Task 5:** Configure and Verify PC `IP Addresses`: Configure `John's` and `Micky's` PCs with `IP addresses`/subnet masks; verify connectivity.

* **Task 6:** Display Switch Information: Display `FastEthernet0/1` interface info and `MAC` address table.

* **Task 7:** Display Running Configuration: Display switch's running configuration.

### Task 1: Connect to the Switch, Explore CLI Modes, and Set System Time

![Figure 1 - Admin PC Connected to Switch Console](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/01-Essential-Switch-Configuration/images/Figure01_Admin_PC_Connected_to_Switch_Console.png)

1. The `Admin PC` was connected to the switch's console port using a `Console Cable` (`Connections > Console`).

2. The `Admin PC's Terminal` application was opened with default settings to access the switch's `CLI`, and `Enter` was pressed to initiate interaction.

3. The command `enable` was entered to transition from user `EXEC` mode (`Switch>`) to privileged `EXEC` mode (`Switch#`).

4. In privileged `EXEC` mode, the switch's system time was set to "`17:30:00 8 October 2024`" using the command `clock set 17:30:00 8 October 2024`.

![Figure 2 - CLI Mode and Clock Set](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/01-Essential-Switch-Configuration/images/Figure02_CLI_Mode_and_Clock_Set.png)

### Task 2: Enter Global Configuration Mode, Set Hostname, and Configure User and Privileged EXEC Passwords

![Figure 3 - Global Config Mode, Hostname, User, and Privileged EXEC Passwords Configured](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/01-Essential-Switch-Configuration/images/Figure03_Global_Config_Mode_Hostname_User_and_Privileged_EXEC_Passwords_Config.png)

1. Global Configuration mode was entered using the command `configure terminal`.

2. The hostname was set to "`S1-Floor1`" with the command `hostname S1-Floor1`.

3. A user named "`Admin`" with the password "`p@nd@`" was created using the command `username Admin password p@nd@`.

4. The privileged `EXEC` mode password was set to "`c!sc0`" with the command `enable password c!sc0`.

### Task 3: Configure Switch Security

![Figure 4 - MOTD Banner and Console Authentication Configuration](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/01-Essential-Switch-Configuration/images/Figure04_MOTD_Banner_Console_Authentication_Configuration.png)

1. Set the `Message of the Day (MOTD)` banner by entering the command `banner motd #Access to this device is for authorized personnel only!#` and pressing `Enter`.

2. Accessed console line configuration by entering `line console 0` and pressing `Enter`.

3. Enforced local credential authentication by typing `login local` and pressing `Enter`.

### Task 4: Encrypt and Save Configurations

![Figure 5 - Exit to Global Config Mode, Encrypt, and Save Configurations](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/01-Essential-Switch-Configuration/images/Figure05_Exit_to_Global_Config_Mode_Encrypt_and_Save_Configurations.png)

1. Entered the `Exit` command to return to Global Configuration Mode.

2. Encrypted all plaintext passwords with the command `service password-encryption`.

3. Exited Global Configuration Mode and saved the configuration by entering `copy running-config startup-config` in `CLI`. When prompted for the destination filename, pressed `Enter` again to confirm the default.

### Task 5: Configure and Verify PC IP Addresses

![Figure 6 - John's PC IP Configuration](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/01-Essential-Switch-Configuration/images/Figure06_Johns_PC_IP_Configuration.png)

1. Configured `John's PC` through its `IP Configuration` window. Set the `IP Address` to `10.0.0.1` and the `Subnet Mask` to `255.0.0.0`.

2. Configured `Micky's PC` the same way: Set the `IP Address` to `10.0.0.2` and the `Subnet Mask` to `255.0.0.0`.

3. Tested Connectivity from `John's PC Command Prompt` with the command `ping 10.0.0.2` and verified connectivity to `Micky's PC`.

![Figure 7 - Micky's PC Ping Test](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/01-Essential-Switch-Configuration/images/Figure07_Mickys_PC_Ping_Test.png)

### Task 6: Display Switch Information

![Figure 8 - Show Interfaces FastEthernet0-1](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/01-Essential-Switch-Configuration/images/Figure08_Show_Interfaces_FastEthernet0-1.png)

1. In the switch's `CLI` from the `Admin PC`, entered the command `show interfaces fastethernet0/1` to display detailed information about the `FastEthernet0/1` interface.

2. Typed the command `show mac-address-table` to display the switch's `MAC address table`.

![Figure 9 - Show MAC Address Table](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/01-Essential-Switch-Configuration/images/Figure09_Show_MAC_Address_Table.png)

### Task 7: Display Running Configuration

![Figure 10 - Show Running-Config](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/01-Essential-Switch-Configuration/images/Figure10_Show_Running_Config.png)

1. Entered the command `show running-config` to review the current configuration.

![Figure 11 - Show Running-Config 2](https://github.com/iagsalazar1-cs/Network-Administration-and-Labs/blob/main/01-Essential-Switch-Configuration/images/Figure11_Show_Running_Config_2.png)
