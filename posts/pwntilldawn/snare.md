<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A  10.150.150.18  -T4  -v -p-

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-05 09:30 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 09:30
Completed NSE at 09:30, 0.00s elapsed
Initiating NSE at 09:30
Completed NSE at 09:30, 0.00s elapsed
Initiating NSE at 09:30
Completed NSE at 09:30, 0.00s elapsed
Initiating Ping Scan at 09:30
Scanning 10.150.150.18 [4 ports]
Completed Ping Scan at 09:30, 0.38s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 09:30
Completed Parallel DNS resolution of 1 host. at 09:30, 0.05s elapsed
Initiating SYN Stealth Scan at 09:30
Scanning 10.150.150.18 [65535 ports]
Discovered open port 22/tcp on 10.150.150.18
Discovered open port 80/tcp on 10.150.150.18
Increasing send delay for 10.150.150.18 from 0 to 5 due to 1727 out of 4316 dropped probes since last increase.
SYN Stealth Scan Timing: About 6.64% done; ETC: 09:38 (0:07:16 remaining)
Increasing send delay for 10.150.150.18 from 5 to 10 due to 11 out of 18 dropped probes since last increase.
SYN Stealth Scan Timing: About 10.51% done; ETC: 09:40 (0:08:39 remaining)
SYN Stealth Scan Timing: About 14.24% done; ETC: 09:41 (0:09:08 remaining)
SYN Stealth Scan Timing: About 29.33% done; ETC: 09:43 (0:08:36 remaining)
SYN Stealth Scan Timing: About 35.96% done; ETC: 09:43 (0:07:57 remaining)
SYN Stealth Scan Timing: About 42.37% done; ETC: 09:43 (0:07:18 remaining)
SYN Stealth Scan Timing: About 48.36% done; ETC: 09:43 (0:06:38 remaining)
SYN Stealth Scan Timing: About 53.84% done; ETC: 09:43 (0:05:58 remaining)
SYN Stealth Scan Timing: About 59.07% done; ETC: 09:43 (0:05:19 remaining)
SYN Stealth Scan Timing: About 64.55% done; ETC: 09:44 (0:04:37 remaining)
SYN Stealth Scan Timing: About 69.72% done; ETC: 09:44 (0:03:58 remaining)
SYN Stealth Scan Timing: About 75.13% done; ETC: 09:44 (0:03:16 remaining)
SYN Stealth Scan Timing: About 80.29% done; ETC: 09:44 (0:02:36 remaining)
SYN Stealth Scan Timing: About 85.55% done; ETC: 09:44 (0:01:55 remaining)
SYN Stealth Scan Timing: About 90.89% done; ETC: 09:44 (0:01:13 remaining)
SYN Stealth Scan Timing: About 96.25% done; ETC: 09:44 (0:00:30 remaining)
Completed SYN Stealth Scan at 09:44, 829.43s elapsed (65535 total ports)
Initiating Service scan at 09:44
Scanning 2 services on 10.150.150.18
Completed Service scan at 09:44, 7.49s elapsed (2 services on 1 host)
Initiating OS detection (try #1) against 10.150.150.18
Retrying OS detection (try #2) against 10.150.150.18
Retrying OS detection (try #3) against 10.150.150.18
Retrying OS detection (try #4) against 10.150.150.18
Retrying OS detection (try #5) against 10.150.150.18
Initiating Traceroute at 09:45
Completed Traceroute at 09:45, 0.32s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 09:45
Completed Parallel DNS resolution of 2 hosts. at 09:45, 0.04s elapsed
NSE: Script scanning 10.150.150.18.
Initiating NSE at 09:45
Completed NSE at 09:45, 5.29s elapsed
Initiating NSE at 09:45
Completed NSE at 09:45, 0.75s elapsed
Initiating NSE at 09:45
Completed NSE at 09:45, 0.00s elapsed
Nmap scan report for 10.150.150.18
Host is up (0.18s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.1 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 2f0e73d4ae73147ec51c1584ef45a4d1 (RSA)
|   256 390b0bc986c98eb52b0c39c763ece210 (ECDSA)
|_  256 f6bfc5035bdfe5e1f4daac1eb207882f (ED25519)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
| http-title: Welcome to my homepage!
|_Requested resource was /index.php?page=home
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.41 (Ubuntu)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=3/5%OT=22%CT=1%CU=33837%PV=Y%DS=2%DC=T%G=Y%TM=6404569C
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=104%GCD=1%ISR=10E%TI=Z%CI=Z%II=I%TS=A)SEQ(
OS:SP=104%GCD=1%ISR=10E%TI=Z%CI=Z%TS=A)OPS(O1=M54DST11NW7%O2=M54DST11NW7%O3
OS:=M54DNNT11NW7%O4=M54DST11NW7%O5=M54DST11NW7%O6=M54DST11)WIN(W1=FE88%W2=F
OS:E88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)ECN(R=Y%DF=Y%T=40%W=FAF0%O=M54DNNSNW
OS:7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF
OS:=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=
OS:%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=
OS:0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RI
OS:PCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 1.748 days (since Fri Mar  3 15:47:51 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=260 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 1723/tcp)
HOP RTT       ADDRESS
1   310.51 ms 10.66.66.1
2   310.56 ms 10.150.150.18

NSE: Script Post-scanning.
Initiating NSE at 09:45
Completed NSE at 09:45, 0.00s elapsed
Initiating NSE at 09:45
Completed NSE at 09:45, 0.00s elapsed
Initiating NSE at 09:45
Completed NSE at 09:45, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 859.03 seconds
           Raw packets sent: 70817 (3.121MB) | Rcvd: 69282 (2.776MB)
```
We have 2 ports  opened here. Port 22 which runs ssh and port 80 which runs http. Our enumeration will be focused on port 80.




























