# Testing and troublehooting Network connectivity

The mostly used tool for checking connectivity is `ping`. This tool is also available on Windows and linux with different options. Ping sends an ICMP echo request to the destination IP and waits for a reply. When the destination IP receives an `ICMP` echo request, it replies with an echo.

Basic syntax `ping [options] destination.com`. This will send an echo request continuously. It wont stop untill `ctrl + c`. Number of ICMP request to be sent can be also specified by option `-c [number of request]`. 

**Some other options:**

* `-i [interval time]` set the interval time between sending requests. Only super user can set this value to less than 0.2 seconds.
* `-q` display the summary only.
* `-t 1` Helps dicovering path the packet takes to travel to the destination. here `1` means the first router to the destination, and the value can be incremented for discovering 2nd, 3rd, 4th and so on routers respectively by specifying the value 2, 3, 4. But once its outside the users ISP, it does not show further details.


### Output
`ping` command resolves the domain to an address. The output may show that the resolved ip shows another domain in output. 

**For example:** `ping google.com -c 4` shows the output `64 bytes from tzdelb-au-in-f14.1e100.net (142.250.182.206): icmp_seq=1 ttl=117 time=29.8 ms`. Here, the IP of google showing another domain `tzdelb-au-in-f14.1e100.net`. This is because multiple domain can be hosted on a single IP address. Ping works as dns resolver here.

**The output of the ping command:**

A simple output: `64 bytes from maa05s22-in-f14.1e100.net (142.250.182.142): icmp_seq=1 ttl=117 time=27.9 ms`

Here,
* `64 bytes` is the packet size
* `maa05s22-in-f14.1e100.net` Is the echo received from which is hosted on same domain as our destination domain.
* `142.250.182.142` IP address of our destination domain.
* `icmp_seq=1` Sequence of packets, if they arrive in serial then they are probably using same paths to travel to the destination.
* `ttl=117` means number of hops or routers between the user and the destination.
* `time=27.9 ms` round trip time or rtt needed for the packet to reach the remote host and for the response to return to the sender. Less means better. If its less than 30 then its excellent, 30 to 50 is OK, 50 to 100 little slow, greater then 100 is slow response and realtime application does not work properly like VOIP phone calls.

If the ping request is successful, it will provide a response and packet loss will be 0%. To prevent reverse DNS lookup while using ping command `-n` option is used. 

## Some easy troubleshooting steps
Few easy and quick troubleshooting scenatios for a small or home network approaches step by step:

### Step 1:
`ping [default gateway]`. If its not working then there is a problem in the LAN. Few scenarios could happen which are:
* User not authenticated to the router
* Dont have correct IP address set
* Router is not correctly configured

If ping to the default gateworks then comes second step ping to public IP address.

### Step 2:
The second step includes `ping` to the public ip (e.g. googles DNS server `8.8.8.8`). If its not working then there is an internet connectivity issue. Maybe the router is not configured correctly. If the router is correctly configured then probably the problem is on the ISP.

### Step 3:
If both step 1 and 2 works then there comes the third step ping to a stable internet domain like `google.com`. If its not working then there is a DNS issue. Few things may happend here:
* The packets getting filtered by DNS
* Not using correct DNS server
* The DNS server is down
* Configuration error related to DNS

> These three steps are appropriate in most cases for small or Home network. In reality, trouble shooting is very complex scenario.
