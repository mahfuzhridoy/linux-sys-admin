# Troubleshooting SSH
### Step 1:
If an ssh connection fails. The first thing that a user need to identify Exact ssh errors. There are many type of errors which are:
* `No route to host` Usually points toward network/routing problem
* `Network is unreachable` Client network rouning.
* `Connection timeout` Network path, firewall, serverdown.
* `Connection refused` Host reachble, but nothing accepting SSH on that port
* `Permission denied(publickey)` Authentication/key problem
* `Permission denied(password)` Password/account/authentication problem
* `Connection reset by peer` Server/firewall/SSH-side termination

#### No route to host:
    ssh: connect to host <IP> port 22: No route to host

Meaning: The client cannot establish a network path to the destination host.

Possible causes:

- Client has a routing/network problem
- Server is unreachable or its network interface is down
- Incorrect IP address
- Firewall or network device is blocking/rejecting the traffic
- Network infrastructure problem

