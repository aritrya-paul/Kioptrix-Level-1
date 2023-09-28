# Kioptrix-Level-1

Kioptrix - 1

Name – Aritrya Paul 

My Setup : 
1) A VMware virtual machine running kali linux
2) Another VM running Kioptrix
3) Both has NAT type Network Adapter

**STEP 1** - First to check the hosts running on our IP address with the shell command : 
            
            netdiscover

![netdiscover](https://github.com/aritrya-paul/Kioptrix-Level-1/assets/129430524/34acb7c8-6efd-44bd-9561-acd384fb4b99)

So, the IP of the host is **192.168.13.131** . 
To check it we can type the command : **enum4linux 192.168.13.131** which shows the information about the target.

![enum4linux](https://github.com/aritrya-paul/Kioptrix-Level-1/assets/129430524/06d7cd18-05bd-40cc-ac60-3c3ee9f1b616)

**STEP 2** - I have used Nmap to run a fast/aggression scan over the network. To do so I have used the command : 

        nmap -sS -A 192.168.13.131

![nmap](https://github.com/aritrya-paul/Kioptrix-Level-1/assets/129430524/b0a57d33-3e35-41d7-aa30-7fa7605fd588)

*-sS is for TCP SYN scan <br>
*-A Decets OS and Services

I have done a bit more recon and enumeration this time. So, I have done a more thorough scan. So, I have used the command : 

      nmap -p- -T4 -A -O -v 192.168.13.131

**The output of the above scan** : 

Starting Nmap 7.94 ( https://nmap.org ) at 2023-09-28 14:07 IST
NSE: Loaded 156 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 14:07
Completed NSE at 14:07, 0.00s elapsed
Initiating NSE at 14:07
Completed NSE at 14:07, 0.00s elapsed
Initiating NSE at 14:07
Completed NSE at 14:07, 0.00s elapsed
Initiating ARP Ping Scan at 14:07
Scanning 192.168.13.131 [1 port]
Completed ARP Ping Scan at 14:07, 0.09s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 14:07
Completed Parallel DNS resolution of 1 host. at 14:07, 0.02s elapsed
Initiating SYN Stealth Scan at 14:07
Scanning 192.168.13.131 [65535 ports]
Discovered open port 139/tcp on 192.168.13.131
Discovered open port 80/tcp on 192.168.13.131
Discovered open port 22/tcp on 192.168.13.131
Discovered open port 443/tcp on 192.168.13.131
Discovered open port 111/tcp on 192.168.13.131
Discovered open port 1024/tcp on 192.168.13.131
Completed SYN Stealth Scan at 14:07, 7.64s elapsed (65535 total ports)
Initiating Service scan at 14:07
Scanning 6 services on 192.168.13.131
Completed Service scan at 14:07, 11.03s elapsed (6 services on 1 host)
Initiating OS detection (try #1) against 192.168.13.131
NSE: Script scanning 192.168.13.131.
Initiating NSE at 14:07
Completed NSE at 14:08, 10.51s elapsed
Initiating NSE at 14:08
Completed NSE at 14:08, 0.10s elapsed
Initiating NSE at 14:08
Completed NSE at 14:08, 0.00s elapsed
Nmap scan report for 192.168.13.131
Host is up (0.00097s latency).
Not shown: 65529 closed tcp ports (reset)
PORT     STATE SERVICE     VERSION
22/tcp   open  ssh         OpenSSH 2.9p2 (protocol 1.99)
| ssh-hostkey: 
|   1024 b8:74:6c:db:fd:8b:e6:66:e9:2a:2b:df:5e:6f:64:86 (RSA1)
|   1024 8f:8e:5b:81:ed:21:ab:c1:80:e1:57:a3:3c:85:c4:71 (DSA)
|_  1024 ed:4e:a9:4a:06:14:ff:15:14:ce:da:3a:80:db:e2:81 (RSA)
|_sshv1: Server supports SSHv1
80/tcp   open  http        Apache httpd 1.3.20 ((Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b)
| http-methods: 
|   Supported Methods: GET HEAD OPTIONS TRACE
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
|_http-title: Test Page for the Apache Web Server on Red Hat Linux
111/tcp  open  rpcbind     2 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2            111/tcp   rpcbind
|   100000  2            111/udp   rpcbind
|   100024  1           1024/tcp   status
|_  100024  1           1024/udp   status
139/tcp  open  netbios-ssn Samba smbd (workgroup: MYGROUP)
443/tcp  open  ssl/https   Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
|_ssl-date: 2023-09-28T08:39:54+00:00; +1m52s from scanner time.
|_http-server-header: Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
| sslv2: 
|   SSLv2 supported
|   ciphers: 
|     SSL2_DES_64_CBC_WITH_MD5
|     SSL2_RC2_128_CBC_WITH_MD5
|     SSL2_RC4_64_WITH_MD5
|     SSL2_RC4_128_WITH_MD5
|     SSL2_RC4_128_EXPORT40_WITH_MD5
|     SSL2_DES_192_EDE3_CBC_WITH_MD5
|_    SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
| http-methods: 
|_  Supported Methods: GET HEAD POST
| ssl-cert: Subject: commonName=localhost.localdomain/organizationName=SomeOrganization/stateOrProvinceName=SomeState/countryName=--
| Issuer: commonName=localhost.localdomain/organizationName=SomeOrganization/stateOrProvinceName=SomeState/countryName=--
| Public Key type: rsa
| Public Key bits: 1024
| Signature Algorithm: md5WithRSAEncryption
| Not valid before: 2009-09-26T09:32:06
| Not valid after:  2010-09-26T09:32:06
| MD5:   78ce:5293:4723:e7fe:c28d:74ab:42d7:02f1
|_SHA-1: 9c42:91c3:bed2:a95b:983d:10ac:f766:ecb9:8766:1d33
|_http-title: 400 Bad Request
1024/tcp open  status      1 (RPC #100024)
MAC Address: 00:0C:29:2E:A7:98 (VMware)
Device type: general purpose
Running: Linux 2.4.X
OS CPE: cpe:/o:linux:linux_kernel:2.4
OS details: Linux 2.4.9 - 2.4.18 (likely embedded)
Uptime guess: 0.036 days (since Thu Sep 28 13:15:35 2023)
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=201 (Good luck!)
IP ID Sequence Generation: All zeros

Host script results:
|_smb2-time: Protocol negotiation failed (SMB2)
| nbstat: NetBIOS name: KIOPTRIX, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| Names:
|   KIOPTRIX<00>         Flags: <unique><active>
|   KIOPTRIX<03>         Flags: <unique><active>
|   KIOPTRIX<20>         Flags: <unique><active>
|   \x01\x02__MSBROWSE__\x02<01>  Flags: <group><active>
|   MYGROUP<00>          Flags: <group><active>
|   MYGROUP<1d>          Flags: <unique><active>
|_  MYGROUP<1e>          Flags: <group><active>
|_clock-skew: 1m51s

TRACEROUTE
HOP RTT     ADDRESS
1   0.97 ms 192.168.13.131

NSE: Script Post-scanning.
Initiating NSE at 14:08
Completed NSE at 14:08, 0.00s elapsed
Initiating NSE at 14:08
Completed NSE at 14:08, 0.00s elapsed
Initiating NSE at 14:08
Completed NSE at 14:08, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 31.99 seconds
           Raw packets sent: 65555 (2.885MB) | Rcvd: 65551 (2.623MB)



Here, To start with HTTP/S. We have both the ports open. **Port 80** is for **http** and **port 443** for **https**. Other findings : 
1] Apache/1.3.20 (Unix)
2] mod_ssl/2.8.4
3] OpenSSL/0.9.6b

I have also got the **Samba port:139**.

I have also got **port 22: the SSH port**. Other findings : 
1] OpenSSH 2.9p2 (protocol 1.99)
2] Sshv1: Server support SSHv1

From the above output we can see that the process is running in netbios-ssn Samba but no exact version is described.


**STEP 3** - I have used searchsploit on openssh 2.9 and Apache 1.2.30 by the command : 

             searchsploit openssh 2.9





                                   








