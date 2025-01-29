# Introduction to the CLI

Cisco IOS - The operating system used on Cisco devices

**CLI - Command Line Interface**

- The interface you use to configure Cisco devices

Cisco devices can be connected to through their console ports. These may come as either RJ47 or USB Mini-B connectors.

**Roll-Over Cable**

The cable used to connect to a cisco device is called a Roll-Over Cable

**Roll-Over Cable Pin Connections**

1 → 8

2 → 7

3 → 6

4 → 5

5 → 4

6 → 3

7 → 2

8 → 1

To access the device a terminal emulator is needed (E.g., PuTTY). Serial > Open

**Settings**

Speed - 9600 bps

Data Bits - 8

Stop Bits - 1

Parity - None

Flow Control - None

**Modes**

User EXEC mode

- Indicated by - HOSTNAME“>”
- Very Limited Access
- Sometimes referred to as USER Mode

If “enable” is typed and entered while in user EXEC mode, the mode will then be switched to **privileged EXEC mode.**

Privileged EXEC Mode

- Indicated by - HOSTNAME”#”
- Provides complete access to view the device’s configuration, restart the device, etc.
- Cannot change the configuration, but can change the time on the device, save the configuration file, etc.

If “configure terminal” is typed and entered while in privileged EXEC mode, the mode will then be switched to **global configuration mode.**

Global Configuration Mode

- Indicated by - HOSTNAME(config)#

Password can be added using - “`enable password PASSWORD`” (Password is case sensitive)

**Configuration Files**

There are two separate configuration files kept on the device at once. These are:

- The Running Config
    - Current, active configuration file on the device. As you enter commands in the CLI, you edit the active
    
- The Start-Up Config
    - The configuration file that will be loaded upon restart of the device

Command - “`show running-config`” can be used to view the running configuration file.

The running-config file can be saved to the startup-config file using the following commands:

- `write`
- `write memory`
- `copy running-config startup-config`
- (NOTE: All these command are run from **privileged EXEC mode**)

Password can be encrypted using the command “`service password-encryption`”. This encrypts the password in **Cisco type 7** encryption type. Despite being encrypted, the password can still easily be cracked. This cracking risk can be reduced by using the “`enable secret PASSWORD`” command, which encrypts the password with an MD5 encryption type, whether the “`service password-encryption`” command has been called or not.

(**NOTE:** If both the “`enable password PASSWORD`” and “`enable secret PASSWORD`” are used, then the password entered with the “`enable password PASSWORD`” will be ignored, and the password entered in the “`enable secret PASSWORD`” command will be used)

`no`

The “no” command can be used to cancel commands in the Cisco CLI, E.g., The command “`no service password-encryption`” will turn off password encryption for all future passwords. 

(**NOTE:** This does not unencrypt the passwords which have already been encrypted)

`run` and `do`

- The `run` command can be used to execute **global configuration mode** commands from **privileged EXEC mode**

- The `do` command can be used to execute **privileged EXEC mode** commands from **global configuration mode**