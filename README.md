# Kioptrix-Level-1

Kioptrix - 1

Name – Aritrya Paul 

My Setup : 
1) A VMware virtual machine running kali linux
2) Another VM running Kioptrix
3) Both has NAT type Network Adapter

**STEP 1** - First to check the hosts running on our IP address with the shell command :   netdiscover

![netdiscover](https://github.com/aritrya-paul/Kioptrix-Level-1/assets/129430524/34acb7c8-6efd-44bd-9561-acd384fb4b99)

So, the IP of the host is **192.168.13.131** . 
To check it we can type the command : **enum4linux 192.168.13.131** which shows the information about the target.

![enum4linux](https://github.com/aritrya-paul/Kioptrix-Level-1/assets/129430524/06d7cd18-05bd-40cc-ac60-3c3ee9f1b616)

**STEP 2** - I have used Nmap to run a fast/aggression scan over the network. To do so I have used the command : 
                                   **nmap -sS -A 192.168.13.131**

![nmap](https://github.com/aritrya-paul/Kioptrix-Level-1/assets/129430524/b0a57d33-3e35-41d7-aa30-7fa7605fd588)

*-sS is for TCP SYN scan
*-A Decets OS and Services

I have done a bit more recon and enumeration this time. So, I have done a more thorough scan. So, I have used the command : 

nmap -p- -T4 -A -O -v 192.168.13.131



                                   








