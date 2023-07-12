## Nmap Scan

```
nmap -sVC -p- -A 192.168.52.217 --open
Starting Nmap 7.93 ( https://nmap.org ) at 2023-07-12 08:07 EDT
Nmap scan report for 192.168.52.217
Host is up (0.0037s latency).
Not shown: 65533 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.10 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 951d828f5ede9a00a80739bdacadd344 (RSA)
|   256 d7b452a2c8fab70ed1a8d070cd6b3690 (ECDSA)
|_  256 dff24f773344d593d77917455aa1368b (ED25519)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-title: Blogger | Home
|_http-server-header: Apache/2.4.18 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.25 seconds

```

## Dirb

```
dirb http://192.168.52.217

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Wed Jul 12 08:08:33 2023
URL_BASE: http://192.168.52.217/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

                                                                             GENERATED WORDS: 4612

---- Scanning URL: http://192.168.52.217/ ----
                                                                                                                                                          ==> DIRECTORY: http://192.168.52.217/assets/
                                                                             ==> DIRECTORY: http://192.168.52.217/css/
                                                                             ==> DIRECTORY: http://192.168.52.217/images/
+ http://192.168.52.217/index.html (CODE:200|SIZE:46199)                    
                                                                             ==> DIRECTORY: http://192.168.52.217/js/
+ http://192.168.52.217/server-status (CODE:403|SIZE:279)                   
                                                                            
---- Entering directory: http://192.168.52.217/assets/ ----
                                                                             (!) WARNING: Directory IS LISTABLE. No need to scan it.
    (Use mode '-w' if you want to scan it anyway)
                                                                            
---- Entering directory: http://192.168.52.217/css/ ----
                                                                             (!) WARNING: Directory IS LISTABLE. No need to scan it.
    (Use mode '-w' if you want to scan it anyway)
                                                                            
---- Entering directory: http://192.168.52.217/images/ ----
                                                                             (!) WARNING: Directory IS LISTABLE. No need to scan it.
    (Use mode '-w' if you want to scan it anyway)
                                                                            
---- Entering directory: http://192.168.52.217/js/ ----
                                                                             (!) WARNING: Directory IS LISTABLE. No need to scan it.
    (Use mode '-w' if you want to scan it anyway)
                                                                               
-----------------
END_TIME: Wed Jul 12 08:08:37 2023
DOWNLOADED: 4612 - FOUND: 2

```

