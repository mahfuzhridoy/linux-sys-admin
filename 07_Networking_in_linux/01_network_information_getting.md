# Getting Information About Network

To get the needed information about the network interfaces, two most common commands are:
- `ifconfig`
- `ip a`

Net tools are not installed by default on the ubuntu os. To install net tools `sudo apt install net-tools`. This two commands can be used for both displaying the information an configuring the network interface. 


### Informations 
Both `ifconfig` and `ip` display same informations. This includes the names of the interfaces and their detailed informations.

#### interface names

* enp0s3: This is a network interface on a pci card where `en` stands for `ethernet`, `p0` means port number 0, and finally `s3` means slot number 3. This is an ethernet connection interface. In older linux distributions, it is called `eth0`

* lo: is a loopback interface. It is a special virtual network interface that allows a computer to communicate with itself. Its most common IPv4 address is `127.0.0.1` and hostname is `localhost`, IPv6 `::1`. 

* wlan0: Is a wireless internet connection interface. 

#### Informations shown

Network interface information is displayed to provide details about the configuration, status, and performance of each network interface available in a Linux system. Different types of interfaces, such as Ethernet interfaces (`eth0`), wireless interfaces (`wlan0`), and the loopback interface (`lo`), may be shown.

The interface name is displayed to identify the specific network device. Its operational status is indicated by flags such as **UP**, **BROADCAST**, **RUNNING**, and **MULTICAST**. The maximum transmission unit (MTU), which represents the maximum size of a packet that can be transmitted, is also shown.

The IPv4 address assigned to the interface is displayed along with the **netmask** and **broadcast address**. The IPv6 address, if configured, is also displayed together with its prefix length and scope information.

The physical address of the network interface is shown as the **MAC address**. The transmission queue length is also displayed to indicate the number of packets that can be queued for transmission.

Network traffic statistics are provided through **RX (Received)** and **TX (Transmitted)** information. The total number of packets and bytes received and transmitted through the interface is displayed.

Error statistics are also provided. Information about **errors, dropped packets, overruns, frame errors, carrier errors, and collisions** is displayed to help identify possible network or hardware problems.

Overall, network interface information is used to monitor the status, configuration, addresses, and communication activity of network interfaces in a Linux system.



### Commands
To display informations, `ifconfig -a` and `ip address show` commands are used. they will produce same output but in different format. without the -a option `ifconfig` will only show the enabled interfaces. On the `ip` command, address is the object that to be managed and show is the command performed on object address.

To see IPv4 and IPv6 address using ip command, `ip -4 address` and `ip -6 address` commands are used respectively.

To get information about a specific interface `ifconfig` or `ip` command is run along with its interface name. Example command: `ifconfig eth0`


### Default Gateway

A **default gateway** is a network device, usually a router, through which packets are forwarded when a specific route to the destination is not available in the routing table.

In Linux, the default gateway is represented by a **default route**, which is commonly displayed as:

* **Destination:** `0.0.0.0`
* **Genmask:** `0.0.0.0`

The default gateway provides a path from the local network to **other networks**, such as the Internet. When a destination does not match any more specific route in the routing table, the packet is sent to the configured default gateway.

A default gateway can be configured for one or more network interfaces. When multiple default routes are available, their **metrics** are used to determine which route should be preferred. Generally, a route with a **lower metric** is preferred over one with a higher metric.

The default gateway can be viewed using commands such as:

```bash
ip route
```

or:

```bash
route -n
```

The default route is typically displayed with the keyword **default** or with `0.0.0.0` as the destination.

Overall, the **default gateway serves as the exit point from a local network to other networks** and is an essential part of IP communication and Linux network configuration.


### DNS
Dns is under the control of `systemd` resolved daemon. This is a service that provides DNS name resolution to local services and applications and it can be configured with netplan, the default network management tool. To see the dns servers the following command is used `systemd-resolve --status`