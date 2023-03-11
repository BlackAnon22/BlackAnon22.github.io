<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 10.129.177.250 -p- -T4 -v

```
[~] Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-12 00:25 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 0.00s elapsed
Initiating Ping Scan at 00:25
Scanning 10.129.178.127 [2 ports]
Completed Ping Scan at 00:25, 0.14s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 00:25
Completed Parallel DNS resolution of 1 host. at 00:25, 0.02s elapsed
DNS resolution of 1 IPs took 0.03s. Mode: Async [#: 1, OK: 0, NX: 1, DR: 0, SF: 0, TR: 1, CN: 0]
Initiating Connect Scan at 00:25
Scanning 10.129.178.127 [2 ports]
Discovered open port 8080/tcp on 10.129.178.127
Discovered open port 22/tcp on 10.129.178.127
Completed Connect Scan at 00:25, 0.19s elapsed (2 total ports)
Initiating Service scan at 00:25
Scanning 2 services on 10.129.178.127
Completed Service scan at 00:25, 7.24s elapsed (2 services on 1 host)
NSE: Script scanning 10.129.178.127.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 6.19s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 0.73s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 0.00s elapsed
Nmap scan report for 10.129.178.127
Host is up, received conn-refused (0.15s latency).
Scanned at 2023-03-12 00:25:10 WAT for 15s

PORT     STATE SERVICE     REASON  VERSION
22/tcp   open  ssh         syn-ack OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 caf10c515a596277f0a80c5c7c8ddaf8 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDKZNtFBY2xMX8oDH/EtIMngGHpVX5fyuJLp9ig7NIC9XooaPtK60FoxOLcRr4iccW/9L2GWpp6kT777UzcKtYoijOCtctNClc6tG1hvohEAyXeNunG7GN+Lftc8eb4C6DooZY7oSeO++PgK5oRi3/tg+FSFSi6UZCsjci1NRj/0ywqzl/ytMzq5YoGfzRzIN3HYdFF8RHoW8qs8vcPsEMsbdsy1aGRbslKA2l1qmejyU9cukyGkFjYZsyVj1hEPn9V/uVafdgzNOvopQlg/yozTzN+LZ2rJO7/CCK3cjchnnPZZfeck85k5sw1G5uVGq38qcusfIfCnZlsn2FZzP2BXo5VEoO2IIRudCgJWTzb8urJ6JAWc1h0r6cUlxGdOvSSQQO6Yz1MhN9omUD9r4A5ag4cbI09c1KOnjzIM8hAWlwUDOKlaohgPtSbnZoGuyyHV/oyZu+/1w4HJWJy6urA43u1PFTonOyMkzJZihWNnkHhqrjeVsHTywFPUmTODb8=
|   256 d51c81c97b076b1cc1b429254b52219f (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBIUJSpBOORoHb6HHQkePUztvh85c2F5k5zMDp+hjFhD8VRC2uKJni1FLYkxVPc/yY3Km7Sg1GzTyoGUxvy+EIsg=
|   256 db1d8ceb9472b0d3ed44b96c93a7f91d (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAICZzUvDL0INOklR7AH+iFw+uX+nkJtcw7V+1AsMO9P7p
8080/tcp open  nagios-nsca syn-ack Nagios NSCA
|_http-title: Home
|_http-open-proxy: Proxy might be redirecting requests
| http-methods: 
|_  Supported Methods: GET HEAD OPTIONS
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 16.19 seconds
```
From our scan we have 2 opened ports, port 22 which runs ssh and port 8080 which runs nagios-nsca. Our enumeration today will be focused on port 8080.
























