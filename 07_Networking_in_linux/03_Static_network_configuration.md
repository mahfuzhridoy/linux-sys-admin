# Static network configuration

Typically The ip addresse are assigned dynamically by DHCP server in most of the cases this which is a router. But a server needs a static IP configuration to avoid single point of failure problem of using a DHCP server. In latest releases of ubuntu, `netplan` is the default network configuration tool to manage network. It uses a `.yaml` file located in the directory `/etc/netplan`. Netplan is a network configuration abstraction layer on Ubuntu. It reads YAML configuration files and then generates configuration for a backend renderer, which actually manages the network.

To configure the network most used tools are `NetworkManager`, and `systemd-networkd`. NetworkManager is mostly used on desktop machines, while `systemd-networkd` is used on servers without a GUI.

### Server network configuration
The setting up of static IP on the server can be divided into steps.

**Step 1 Disabling NetworkManager:**

 The network interface can be managed either by NetworkManager or systemd but not by both of them at the same time. Disabling it by command `systemctl stop NetworkManager`. The disabling it so it won't start while booting: `systemctl stop NetworkManager`. To check if it is disabled and wont restart `systemctl status NetworkManager` and if service is disabled, it wont start automatically.

**Step 2 Creating yaml file on /etc/netplan:**

If no longer using NetworkManager, removing or saving The existing yaml file for network manager as backup by renaming it with .bak extension or an appended `.` to make it hidden file.

Then creatign a config file `nano /etc/netplan/[file-name].yaml`. Then adding the configuration yaml text:
```text
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      dhcp4: false
      addresses:
        - 192.168.0.22/24
      gateway: "192.168.0.1"
      nameservers:
        addresses:
          - "8.8.8.8"
          - "8.8.4.4"
```

> **Explanation:** The network configuration yaml file starts with the network keyword. After that atleast 3 requirements: version of the network configuration format, renderer which is networkd here, and the device type here ethernet. If the device type was wireless then here it should have been wifis instead of ethernets. Under the device type one or more interfaces can be configured. Here only the enp0s3 interface is configured. The dhcp4 is false here to disable dynamic ip. The the ip addresses, gateway, and name servers are specified. 


**Step 3 applying the changes**

Once the file is written, The changes should bbe applied with the command: `netplan apply`. Verifying the changes with `ifconfig` and `route` command

> **[Note: Yaml syntax take two white space indentation by default. Without this indentation, the yaml file will give an error. There are some online yaml validators that can be used to validate the written file.]**