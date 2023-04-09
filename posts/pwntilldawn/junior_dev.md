# Recon

## PortScanning

command:```sudo nmap -A 10.150.150.38 -T4  -v -Pn -p-```

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-04-09 14:10 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 14:10
Completed NSE at 14:10, 0.00s elapsed
Initiating NSE at 14:10
Completed NSE at 14:10, 0.00s elapsed
Initiating NSE at 14:10
Completed NSE at 14:10, 0.00s elapsed
Initiating Parallel DNS resolution of 1 host. at 14:10
Completed Parallel DNS resolution of 1 host. at 14:10, 0.03s elapsed
Initiating SYN Stealth Scan at 14:10
Scanning 10.150.150.38 [65535 ports]
Discovered open port 22/tcp on 10.150.150.38
Increasing send delay for 10.150.150.38 from 0 to 5 due to 801 out of 2002 dropped probes since last increase.
Increasing send delay for 10.150.150.38 from 5 to 10 due to 11 out of 22 dropped probes since last increase.
SYN Stealth Scan Timing: About 5.50% done; ETC: 14:19 (0:08:52 remaining)
SYN Stealth Scan Timing: About 8.86% done; ETC: 14:21 (0:10:27 remaining)
SYN Stealth Scan Timing: About 20.33% done; ETC: 14:22 (0:09:52 remaining)
SYN Stealth Scan Timing: About 28.69% done; ETC: 14:23 (0:09:14 remaining)
SYN Stealth Scan Timing: About 35.51% done; ETC: 14:23 (0:08:34 remaining)
SYN Stealth Scan Timing: About 40.51% done; ETC: 14:23 (0:07:53 remaining)
SYN Stealth Scan Timing: About 45.47% done; ETC: 14:23 (0:07:13 remaining)
SYN Stealth Scan Timing: About 50.50% done; ETC: 14:23 (0:06:32 remaining)
SYN Stealth Scan Timing: About 55.85% done; ETC: 14:23 (0:05:49 remaining)
SYN Stealth Scan Timing: About 60.94% done; ETC: 14:23 (0:05:08 remaining)
SYN Stealth Scan Timing: About 66.10% done; ETC: 14:23 (0:04:27 remaining)
SYN Stealth Scan Timing: About 71.44% done; ETC: 14:23 (0:03:45 remaining)
SYN Stealth Scan Timing: About 76.43% done; ETC: 14:23 (0:03:05 remaining)
SYN Stealth Scan Timing: About 81.58% done; ETC: 14:23 (0:02:25 remaining)
Discovered open port 30609/tcp on 10.150.150.38
SYN Stealth Scan Timing: About 86.71% done; ETC: 14:23 (0:01:45 remaining)
SYN Stealth Scan Timing: About 91.72% done; ETC: 14:23 (0:01:05 remaining)
Completed SYN Stealth Scan at 14:23, 806.19s elapsed (65535 total ports)
Initiating Service scan at 14:23
Scanning 2 services on 10.150.150.38
Completed Service scan at 14:23, 11.91s elapsed (2 services on 1 host)
Initiating OS detection (try #1) against 10.150.150.38
Retrying OS detection (try #2) against 10.150.150.38
Retrying OS detection (try #3) against 10.150.150.38
Retrying OS detection (try #4) against 10.150.150.38
Retrying OS detection (try #5) against 10.150.150.38
Initiating Traceroute at 14:24
Completed Traceroute at 14:24, 0.22s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 14:24
Completed Parallel DNS resolution of 2 hosts. at 14:24, 0.06s elapsed
NSE: Script scanning 10.150.150.38.
Initiating NSE at 14:24
Completed NSE at 14:24, 4.91s elapsed
Initiating NSE at 14:24
Completed NSE at 14:24, 0.72s elapsed
Initiating NSE at 14:24
Completed NSE at 14:24, 0.00s elapsed
Nmap scan report for 10.150.150.38
Host is up (0.16s latency).
Not shown: 65523 closed tcp ports (reset)
PORT      STATE    SERVICE        VERSION
22/tcp    open     ssh            OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey: 
|   2048 646302cb00444a0f951a348d4e60381c (RSA)
|   256 0a6e1095de3d6d4b985ff0cfcbf5799e (ECDSA)
|_  256 0804040851d2b4a403bb02712f660969 (ED25519)
2494/tcp  filtered bmc-ar
2723/tcp  filtered watchdog-nt
4257/tcp  filtered vrml-multi-use
30609/tcp open     http           Jetty 9.4.27.v20200227
|_http-title: Site doesn't have a title (text/html;charset=utf-8).
| http-robots.txt: 1 disallowed entry 
|_/
|_http-favicon: Unknown favicon MD5: 23E8C7BD78E8CD826C5A6073B15068B1
|_http-server-header: Jetty(9.4.27.v20200227)
32764/tcp filtered unknown
35194/tcp filtered unknown
36062/tcp filtered unknown
41421/tcp filtered unknown
44696/tcp filtered unknown
45647/tcp filtered unknown
48256/tcp filtered unknown
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=4/9%OT=22%CT=1%CU=38678%PV=Y%DS=2%DC=T%G=Y%TM=6432BC81
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=FF%GCD=1%ISR=FE%TI=Z%CI=Z%II=I%TS=C)OPS(O1
OS:=M54DST11NW7%O2=M54DST11NW7%O3=M54DNNT11NW7%O4=M54DST11NW7%O5=M54DST11NW
OS:7%O6=M54DST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)ECN(R=
OS:Y%DF=Y%T=40%W=FAF0%O=M54DNNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%R
OS:D=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%
OS:DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%
OS:O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=4
OS:0%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 5.088 days (since Tue Apr  4 12:17:12 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=255 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 3306/tcp)
HOP RTT       ADDRESS
1   216.14 ms 10.66.66.1
2   216.14 ms 10.150.150.38

NSE: Script Post-scanning.
Initiating NSE at 14:24
Completed NSE at 14:24, 0.00s elapsed
Initiating NSE at 14:24
Completed NSE at 14:24, 0.00s elapsed
Initiating NSE at 14:24
Completed NSE at 14:24, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 840.51 seconds
           Raw packets sent: 70444 (3.104MB) | Rcvd: 67808 (2.716MB)
```
From our scan we have more filtered ports compared to open ports. The open ports here are port 22 which runs ssh and port 30609 which runs http. Our enumeration today will be focused on port 30609.































