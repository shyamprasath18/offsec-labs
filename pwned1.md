# Information Gathering 

## Nmap Scan

```
nmap -sVC -A -p- 192.168.59.95
Starting Nmap 7.93 ( https://nmap.org ) at 2023-08-27 03:09 EDT
Nmap scan report for 192.168.59.95
Host is up (0.0038s latency).
Not shown: 65532 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
22/tcp open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey: 
|   2048 fecd90197491aef564a8a5e86f6eef7e (RSA)
|   256 813293bded9be798af2506795fde915d (ECDSA)
|_  256 dd72745d4d2da3623e81af0951e0144a (ED25519)
80/tcp open  http    Apache httpd 2.4.38 ((Debian))
|_http-title: Pwned....!!
|_http-server-header: Apache/2.4.38 (Debian)
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 9.30 seconds

```
## Inspect Source code 

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/61f0e02f-2817-45dc-957f-023c085f6d92)

## Robots.txt

```
# Group 1

User-agent: *
Allow: /nothing
Allow: /hidden_text
```

- In the /hidden_text we got the list of dirs
  ![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/beb3d5d4-0ec5-4657-97ba-6dfe06abb351)

