This file contains the cheat sheet for those who wants to take the eJPTv2 exam. So you can just use this for your referencing.


# Discovering hosts available on a network

## Get the IP address of your machine
```sh
$ ifconfig
192.168.56.5
```
## Using either netdiscover or nmap to scan for hosts available on the subnet
```
$ netdiscover -r 192.168.56.0/24
```
or
```
$ nmap -sV 192.168.56.0/24 -v
```
