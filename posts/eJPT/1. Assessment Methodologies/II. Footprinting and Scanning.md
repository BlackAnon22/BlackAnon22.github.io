
<h2>Mapping a Network</h2>
>Arp(Address Resolution Protocol), it resolves IP to MAC

>ICMP(internet control message protocol), used for diagonizing networks.

>Traceroute shows the point between you or the destination and source

>Ping sends a type 8 echo request

<h4>Wireshark</h4>

![[Pasted image 20230628113843.png]]

<h4>Arp-Scan</h4>
```
sudo arp-scan -I wlan0 -g 192.168.160.0/24

-I - interface
-g - generate
```
![[Pasted image 20230628114231.png]]

<h4>Ping</h4>
```
ping 192.168.160.203
```
![[Pasted image 20230628114450.png]]

<h4>fping</h4>
Send pings to multiple hosts at one time
```
fping -I wlan0 -g 192.168.160.0/24 -a

-a - alive
```

```
fping -I wlan0 -g 192.168.160.0/24 -a 2>/dev/null

This won't print out the errors
```
![[Pasted image 20230628115402.png]]

***Getting live IP address using wireshark![[Pasted image 20230704100524.png]]
Then
Statistics>Endpoints
![[Pasted image 20230704100633.png]]
![[Pasted image 20230704100716.png]]


<h4>Port Scanning</h4>

***Connect to TCP***

The normal tcp 3 way handshake,  if we connect we send a ***syn***, we get a ***syn+ack***, we send an ***ack*** , we know that the port is open, then we send a ***rst+ack***, just to close the connection.

***Connect to TCP: Stealth scan***

Sends a ***syn***, gets a ***syn+ack*** in response and rather than finishing the connection it sends the ***rst*** just to close the connection. So, when it returns the syn+ack it knows the port is opened

***Connect to TCP: Service Version***

We do the 3 way handshake, we send a ***syn***, get a ***syn+ack***, we send an ***ack***, with the ack we grab a ***banner*** then we send a ***rst+ack*** to close the connection. 


<h4>Nmap Host Discovery</h4>
To get service version for udp ports 
```
nmap -sUV $ip -v -p 1-250
```
