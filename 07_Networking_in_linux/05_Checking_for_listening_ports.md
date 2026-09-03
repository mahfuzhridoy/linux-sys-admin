# Checking for listening ports
While troubleshooting the network issue, One of the first thing should be done is checking if the server application is listening on a specific port of the machine. Most used tool for finding the opening ports are `netstat` and `ss`. The netstat is a little bit older than ss. Basic command: `sudo netstat -tupan` or `ss -tupan`. Both shows the same result. 

Here, The options `tupan` means

* `t` shows tcp ports
* `u` for showing udp ports
* `p` for process ID
* `a` for all ports which are listening and not listening
* `n` for numerical addresses

**Sample output:**
```text
Netid       State        Recv-Q      Send-Q   Local Address:Port         Peer Address:Port      Process                                               
udp          ESTAB       0           0        192.168.31.109%wlan0:68    192.168.31.1:67        users:(("NetworkManager",pid=822,fd=34))
```

If the local addresses column shows `0.0.0.0` or `:::`(IPv6) as an ip address, This means its listening on all IP addresses of the host. The output can be filtered and checka  specific port or address or anything else with the help of grep command. Example command: `sudo ss -tupan | grep ":22"` for checking the port 22 only.

## Using lsof (list open files)

`lsof` stands for list open files. This is a very useful command for a system administrator. To list all the files that are open in the system by any process `lsof` without any argument or option is run. 

The output can be further filtered. To see all the files open by a specific user `lsof -u [user]` command can be used. Also negation can be used to find open files that are opened by anyone but not the specified user with command `lsof -u ^user1`.

To list all the files open by a specific process `-c [process name]` option is used. Example command: `lsof -c nginx` 


### Watching ports using `lsof`
**To see the files which have open tcp ports:**
> sudo lsof -iTCP -sTCP:LISTEN -nP
Here in this command line:
* `-iTCP` Display only TCP network connection
* `-sTCP:LISTEN` Sows only TCP port in the listening state.
* `-nP` Show the ports and hosts in numeric format.

**To see files that are open in a specific port:**
> sudo lsof -iTCP:22 -sTCP:LISTEN
Here, `-iTCP:22` option specified to port 22 only.

>Note: All these command are used to scan the localhost only. 

## Scanning other systems

Any systems that has an active internet connection can be scanned with `telnet` and `nmap` command. Example command: `telnet google.com 443`. This will look for open 443 port on google.com. 

We can do the same with `nmap`. This is a very useful tool and basic command: `nmap [address]`. This will scan for most used ports. But the port can also be specified by `-p` option. To see the version `-sV` option is used.