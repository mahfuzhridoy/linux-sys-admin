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


### Commands
To display informations, `ifconfig -a` and `ip address show` commands are used. they will produce same output but in different format. without the -a option `ifconfig` will only show the enabled interfaces. On the `ip` command, address is the object that to be managed and show is the command performed on object address.

To see IPv4 and IPv6 address using ip command, `ip -4 address` and `ip -6 address` commands are used respectively.