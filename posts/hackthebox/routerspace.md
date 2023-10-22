# Box: RouterSpace
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.74.1 -v -p- -T4```

```
Nmap scan report for 10.129.74.1
Host is up (0.30s latency).
Not shown: 65533 filtered tcp ports (no-response)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     (protocol 2.0)
| ssh-hostkey: 
|   3072 f4:e4:c8:0a:a6:af:66:93:af:69:5a:a9:bc:75:f9:0c (RSA)
|   256 7f:05:cd:8c:42:7b:a9:4a:b2:e6:35:2c:c4:59:78:02 (ECDSA)
|_  256 2f:d7:a8:8b:be:2d:10:b0:c9:b4:29:52:a8:94:24:78 (ED25519)
| fingerprint-strings: 
|   NULL: 
|_    SSH-2.0-RouterSpace Packet Filtering V1
80/tcp open  http
|_http-title: RouterSpace
|_http-favicon: Unknown favicon MD5: 0105EF27FE7AC7C7EF9124D87E116EB4
|_http-trane-info: Problem with XML parsing of /evox/about
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
| fingerprint-strings: 
|   FourOhFourRequest: 
|     HTTP/1.1 200 OK
|     X-Powered-By: RouterSpace
|     X-Cdn: RouterSpace-24490
|     Content-Type: text/html; charset=utf-8
|     Content-Length: 63
|     ETag: W/"3f-rTDNok1EXG54T5nR1Khs7RjQRVw"
|     Date: Sun, 22 Oct 2023 19:45:20 GMT
|     Connection: close
|     Suspicious activity detected !!! {RequestID: h1u x9 Iz l }
|   GetRequest: 
|     HTTP/1.1 200 OK
|     X-Powered-By: RouterSpace
|     X-Cdn: RouterSpace-59697
|     Accept-Ranges: bytes
|     Cache-Control: public, max-age=0
|     Last-Modified: Mon, 22 Nov 2021 11:33:57 GMT
|     ETag: W/"652c-17d476c9285"
|     Content-Type: text/html; charset=UTF-8
|     Content-Length: 25900
|     Date: Sun, 22 Oct 2023 19:45:18 GMT
|     Connection: close
|     <!doctype html>
|     <html class="no-js" lang="zxx">
|     <head>
|     <meta charset="utf-8">
|     <meta http-equiv="x-ua-compatible" content="ie=edge">
|     <title>RouterSpace</title>
|     <meta name="description" content="">
|     <meta name="viewport" content="width=device-width, initial-scale=1">
|     <link rel="stylesheet" href="css/bootstrap.min.css">
|     <link rel="stylesheet" href="css/owl.carousel.min.css">
|     <link rel="stylesheet" href="css/magnific-popup.css">
|     <link rel="stylesheet" href="css/font-awesome.min.css">
|     <link rel="stylesheet" href="css/themify-icons.css">
|   HTTPOptions: 
|     HTTP/1.1 200 OK
|     X-Powered-By: RouterSpace
|     X-Cdn: RouterSpace-90028
|     Allow: GET,HEAD,POST
|     Content-Type: text/html; charset=utf-8
|     Content-Length: 13
|     ETag: W/"d-bMedpZYGrVt1nR4x+qdNZ2GqyRo"
|     Date: Sun, 22 Oct 2023 19:45:19 GMT
|     Connection: close
|     GET,HEAD,POST
|   RTSPRequest, X11Probe: 
|     HTTP/1.1 400 Bad Request
|_    Connection: close
2 services unrecognized despite returning data. If you know the service/version, please submit the following fingerprints at https://nmap.org/cgi-bin/submit.cgi?new-service :
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port22-TCP:V=7.94%I=7%D=10/22%Time=65357BCD%P=x86_64-pc-linux-gnu%r(NUL
SF:L,29,"SSH-2\.0-RouterSpace\x20Packet\x20Filtering\x20V1\r\n");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port80-TCP:V=7.94%I=7%D=10/22%Time=65357BCF%P=x86_64-pc-linux-gnu%r(Get
SF:Request,33E0,"HTTP/1\.1\x20200\x20OK\r\nX-Powered-By:\x20RouterSpace\r\
SF:nX-Cdn:\x20RouterSpace-59697\r\nAccept-Ranges:\x20bytes\r\nCache-Contro
SF:l:\x20public,\x20max-age=0\r\nLast-Modified:\x20Mon,\x2022\x20Nov\x2020
SF:21\x2011:33:57\x20GMT\r\nETag:\x20W/\"652c-17d476c9285\"\r\nContent-Typ
SF:e:\x20text/html;\x20charset=UTF-8\r\nContent-Length:\x2025900\r\nDate:\
SF:x20Sun,\x2022\x20Oct\x202023\x2019:45:18\x20GMT\r\nConnection:\x20close
SF:\r\n\r\n<!doctype\x20html>\n<html\x20class=\"no-js\"\x20lang=\"zxx\">\n
SF:<head>\n\x20\x20\x20\x20<meta\x20charset=\"utf-8\">\n\x20\x20\x20\x20<m
SF:eta\x20http-equiv=\"x-ua-compatible\"\x20content=\"ie=edge\">\n\x20\x20
SF:\x20\x20<title>RouterSpace</title>\n\x20\x20\x20\x20<meta\x20name=\"des
SF:cription\"\x20content=\"\">\n\x20\x20\x20\x20<meta\x20name=\"viewport\"
SF:\x20content=\"width=device-width,\x20initial-scale=1\">\n\n\x20\x20\x20
SF:\x20<link\x20rel=\"stylesheet\"\x20href=\"css/bootstrap\.min\.css\">\n\
SF:x20\x20\x20\x20<link\x20rel=\"stylesheet\"\x20href=\"css/owl\.carousel\
SF:.min\.css\">\n\x20\x20\x20\x20<link\x20rel=\"stylesheet\"\x20href=\"css
SF:/magnific-popup\.css\">\n\x20\x20\x20\x20<link\x20rel=\"stylesheet\"\x2
SF:0href=\"css/font-awesome\.min\.css\">\n\x20\x20\x20\x20<link\x20rel=\"s
SF:tylesheet\"\x20href=\"css/themify-icons\.css\">\n\x20")%r(HTTPOptions,1
SF:08,"HTTP/1\.1\x20200\x20OK\r\nX-Powered-By:\x20RouterSpace\r\nX-Cdn:\x2
SF:0RouterSpace-90028\r\nAllow:\x20GET,HEAD,POST\r\nContent-Type:\x20text/
SF:html;\x20charset=utf-8\r\nContent-Length:\x2013\r\nETag:\x20W/\"d-bMedp
SF:ZYGrVt1nR4x\+qdNZ2GqyRo\"\r\nDate:\x20Sun,\x2022\x20Oct\x202023\x2019:4
SF:5:19\x20GMT\r\nConnection:\x20close\r\n\r\nGET,HEAD,POST")%r(RTSPReques
SF:t,2F,"HTTP/1\.1\x20400\x20Bad\x20Request\r\nConnection:\x20close\r\n\r\
SF:n")%r(X11Probe,2F,"HTTP/1\.1\x20400\x20Bad\x20Request\r\nConnection:\x2
SF:0close\r\n\r\n")%r(FourOhFourRequest,125,"HTTP/1\.1\x20200\x20OK\r\nX-P
SF:owered-By:\x20RouterSpace\r\nX-Cdn:\x20RouterSpace-24490\r\nContent-Typ
SF:e:\x20text/html;\x20charset=utf-8\r\nContent-Length:\x2063\r\nETag:\x20
SF:W/\"3f-rTDNok1EXG54T5nR1Khs7RjQRVw\"\r\nDate:\x20Sun,\x2022\x20Oct\x202
SF:023\x2019:45:20\x20GMT\r\nConnection:\x20close\r\n\r\nSuspicious\x20act
SF:ivity\x20detected\x20!!!\x20{RequestID:\x20\x20h1u\x20x9\x20\x20Iz\x20\
SF:x20l\x20\x20}\n");
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose|specialized
Running (JUST GUESSING): Linux 5.X (91%), Crestron 2-Series (85%)
OS CPE: cpe:/o:linux:linux_kernel:5.0 cpe:/o:crestron:2_series
Aggressive OS guesses: Linux 5.0 (91%), Crestron XPanel control system (85%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 76.299 days (since Mon Aug  7 13:35:19 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=263 (Good luck!)
IP ID Sequence Generation: All zeros

TRACEROUTE (using port 22/tcp)
HOP RTT       ADDRESS
1   200.89 ms 10.10.14.1
2   207.60 ms 10.129.74.1

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun Oct 22 20:46:22 2023 -- 1 IP address (1 host up) scanned in 452.73 seconds
```
From our scan we have 2 open ports, port 22 which runs the ssh service and port 80 which runs the http service. Our enumeration today will be focused on port 80.



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/76165fc9-a548-47e1-8c14-dc870e8b8d96)

Clicking om the download button, you get this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7b59a0d2-8e1d-4f6f-b229-c94140c93784)

After downloading the file, we'll 
