# Network configuration
While configuring the network using ifconfig or ip, the command should be run using `root` priviledge. 

> Note: Do not run the following commands on a remote system. The following command are for practice on local host only. Disabling an interface will terminate the ssh connection.

#### Taking down an interface
Useful command `ifconfig [interfce name] down`. This will disable the interface that are specified to the command. Example command: `ifconfig wlan0 up`. To check `ifconfig -a` command can be run. **Note: `ifconfig` alone only show the active interfaces. -a shoud be used in case of checking all interfaces**

Same works can be done with the ip command. Example command: `ip link set enps03 down`. and checking `ip link show dev enp0s3`

#### Activating the interface
Useful command `ifconfig [interface name] up`. This will activate the interface. Example command: `ifconfig wlan0 up`. Checking can be done by running `ifconfig -a`.

Same works can be done with the ip command. Example command: `ip link set enps03 up`.  and checking `ip link show dev enp0s3`


## Configuring the network
> Note: Changing the network configuration with ifconfig and ip command is not persistant. Restarting will change all the configuration to default. For a permanent change in settings, distro specific configuration file (netplan for ubuntu) should be edited.

### Changing IP
**With ifconfig**

`ifconfig [interface name] [new ip]/[netmask] up`. Example commnad:  `ifconfig wlan0 192.168.0.111/24 up`. 

**With ip**

To chnage the ip address with `ip` command, the assigned ip of the interface must be removed first. Removing the ip `ip address del [assigned ip]/[mask] dev [interface name]`. Example command: `ip address del 192.168.0.111/24 dev wlan0`. once the previous ip is deleted, new ip can be assigned now using ip command with example command: ``ip address add 192.168.0.111/24 dev wlan0`.

### Changing routing table default gateway
**with route command**

Checking out the default gateway `route -n`. A capital `G` in flags column indicates the default gateway. To change a default gateway, the configured one must be removed first. This can be done with `route del default gw [gateway ip]`. Example command: `route del default gw 192.168.0.1`. The a new gateway ip can be added with `route add default gw 192.168.0.1`.

**With ip command**

First to check the default gateway `ip route show`. Then removing the defaultwith `ip route del default`. And the last step adding new ip `ip route add default via 192.168.0.1`


### Changing the MAC address of an interface
**With ifconfig command**

To change MAC, The interface should be disabled first. Easy command for disabling the interface `ifconfig wlan0 down`. Then Assign the new MAC `ifconfig wlan0 hw ether 00:00:00:00:00:00`. Lastly, reactivating the interface.

**With ip command**

While changing the MAC with ip command, there is no need to take down the interface. This can be done directly with `ip link set dev wlan0 00:00:00:00:00:00`
