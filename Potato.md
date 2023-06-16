## Ping Check
```
ping 192.168.52.101
PING 192.168.52.101 (192.168.52.101) 56(84) bytes of data.
64 bytes from 192.168.52.101: icmp_seq=1 ttl=63 time=0.359 ms
64 bytes from 192.168.52.101: icmp_seq=2 ttl=63 time=0.257 ms
64 bytes from 192.168.52.101: icmp_seq=3 ttl=63 time=0.249 ms
^C
--- 192.168.52.101 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2030ms
rtt min/avg/max/mdev = 0.249/0.288/0.359/0.050 ms
```

## Nmap Scan

```
nmap -sV -Pn -p- 192.168.52.101 --open -A
Starting Nmap 7.93 ( https://nmap.org ) at 2023-06-16 10:34 EDT
Stats: 0:00:25 elapsed; 0 hosts completed (1 up), 1 undergoing Connect Scan
Connect Scan Timing: About 97.75% done; ETC: 10:35 (0:00:00 remaining)
Stats: 0:00:40 elapsed; 0 hosts completed (1 up), 1 undergoing Connect Scan
Connect Scan Timing: About 98.74% done; ETC: 10:35 (0:00:00 remaining)
Stats: 0:01:52 elapsed; 0 hosts completed (1 up), 1 undergoing Script Scan
NSE Timing: About 91.67% done; ETC: 10:36 (0:00:02 remaining)
Nmap scan report for 192.168.52.101
Host is up (0.00047s latency).
Not shown: 60855 closed tcp ports (conn-refused), 4677 filtered tcp ports (no-response)
Some closed ports may be reported as filtered due to --defeat-rst-ratelimit
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.1 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 ef240eabd2b316b44b2e27c05f48798b (RSA)
|   256 f2d8353f4959858507e6a20e657a8c4b (ECDSA)
|_  256 0b2389c3c026d5645e93b7baf5147f3e (ED25519)
80/tcp   open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-title: Potato company
|_http-server-header: Apache/2.4.41 (Ubuntu)
2112/tcp open  ftp
| fingerprint-strings: 
|   GenericLines: 
|     220 ProFTPD Server (Debian) [::ffff:192.168.52.101]
|     Invalid command: try being more creative
|_    Invalid command: try being more creative
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port2112-TCP:V=7.93%I=7%D=6/16%Time=648C7343%P=x86_64-pc-linux-gnu%r(Ge
SF:nericLines,91,"220\x20ProFTPD\x20Server\x20\(Debian\)\x20\[::ffff:192\.
SF:168\.52\.101\]\r\n500\x20Invalid\x20command:\x20try\x20being\x20more\x2
SF:0creative\r\n500\x20Invalid\x20command:\x20try\x20being\x20more\x20crea
SF:tive\r\n");
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 122.96 seconds

```

## Dirb scan 
```
dirb http://192.168.52.101/

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Fri Jun 16 10:40:31 2023
URL_BASE: http://192.168.52.101/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

                                                                             GENERATED WORDS: 4612

---- Scanning URL: http://192.168.52.101/ ----
                                                                                                                                                          ==> DIRECTORY: http://192.168.52.101/admin/
+ http://192.168.52.101/index.php (CODE:200|SIZE:245)                       
+ http://192.168.52.101/server-status (CODE:403|SIZE:279)                   
                                                                            
---- Entering directory: http://192.168.52.101/admin/ ----
                                                                             + http://192.168.52.101/admin/index.php (CODE:200|SIZE:466)                 
                                                                             ==> DIRECTORY: http://192.168.52.101/admin/logs/
                                                                            
---- Entering directory: http://192.168.52.101/admin/logs/ ----
                                                                             (!) WARNING: Directory IS LISTABLE. No need to scan it.
    (Use mode '-w' if you want to scan it anyway)
                                                                               
-----------------
END_TIME: Fri Jun 16 10:40:34 2023
DOWNLOADED: 9224 - FOUND: 3

```

## Pages Found

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/f71f0b78-9bca-4801-8593-6123b9f845fb)

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/39d9c47a-5612-4826-b597-5f08d848f168)

## SSH bruteforce using Hydra

- tried using hydra to bruteforce SSH login , but no use its takes an hours
`hydra -l admin -P /usr/share/wordlists/rockyou.txt 192.168.52.101 ssh`

## FTP anon

- there are two files found , 1. welcome.msg , 2.index.php.bak
- In index.php.bak , username and pass field has been check by strcmp

## Exploiting strcmp








