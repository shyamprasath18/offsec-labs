# Nmap Scan
```
nmap -sCV -p- -Pn 192.168.56.193 --open
Starting Nmap 7.94 ( https://nmap.org ) at 2023-10-14 11:46 EDT
Nmap scan report for 192.168.56.193
Host is up (0.00077s latency).
Not shown: 65531 closed tcp ports (conn-refused)
PORT      STATE SERVICE VERSION
22/tcp    open  ssh     OpenSSH 6.0p1 Debian 4+deb7u7 (protocol 2.0)
| ssh-hostkey: 
|   1024 c4:d6:59:e6:77:4c:22:7a:96:16:60:67:8b:42:48:8f (DSA)
|   2048 11:82:fe:53:4e:dc:5b:32:7f:44:64:82:75:7d:d0:a0 (RSA)
|_  256 3d:aa:98:5c:87:af:ea:84:b8:23:68:8d:b9:05:5f:d8 (ECDSA)
80/tcp    open  http    Apache httpd 2.2.22 ((Debian))
| http-robots.txt: 36 disallowed entries (15 shown)
| /includes/ /misc/ /modules/ /profiles/ /scripts/ 
| /themes/ /CHANGELOG.txt /cron.php /INSTALL.mysql.txt 
| /INSTALL.pgsql.txt /INSTALL.sqlite.txt /install.php /INSTALL.txt 
|_/LICENSE.txt /MAINTAINERS.txt
|_http-server-header: Apache/2.2.22 (Debian)
|_http-generator: Drupal 7 (http://drupal.org)
|_http-title: Welcome to Drupal Site | Drupal Site
111/tcp   open  rpcbind 2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100024  1          35685/udp6  status
|   100024  1          40238/tcp   status
|   100024  1          56691/udp   status
|_  100024  1          58362/tcp6  status
40238/tcp open  status  1 (RPC #100024)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 17.33 seconds

```

- Accessing the web page gives the details on Drupal - a free and open-source web content management system written in PHP

- For scanning the Drupal websites (Plugin based scanner) found called Droopescan

# Droopescan - Drupal website

```
 droopescan scan drupal -u http://192.168.240.193/ -t 32

[+] Plugins found:
    ctools http://192.168.240.193/sites/all/modules/ctools/
        http://192.168.240.193/sites/all/modules/ctools/LICENSE.txt
        http://192.168.240.193/sites/all/modules/ctools/API.txt
    views http://192.168.240.193/sites/all/modules/views/
        http://192.168.240.193/sites/all/modules/views/README.txt
        http://192.168.240.193/sites/all/modules/views/LICENSE.txt
    profile http://192.168.240.193/modules/profile/
    php http://192.168.240.193/modules/php/
    image http://192.168.240.193/modules/image/

[+] Themes found:
    seven http://192.168.240.193/themes/seven/
    garland http://192.168.240.193/themes/garland/

[+] Possible version(s):
    7.22
    7.23
    7.24
    7.25
    7.26

[+] Possible interesting urls found:
    Default admin - http://192.168.240.193/user/login
```

#Finding Creds for Mysql

- flag1 leads to coonfig file and also checked the flag4 in /etc/passwd it leads to root flag in root directory.

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/6c9d2e75-2985-4858-8691-a3facec85183)

```
/**
 *
 * flag2
 * Brute force and dictionary attacks aren't the
 * only ways to gain access (and you WILL need access).
 * What can you do with these credentials?
 *
 */

$databases = array (
  'default' => 
  array (
    'default' => 
    array (
      'database' => 'drupaldb',
      'username' => 'dbuser',
      'password' => 'R0ck3t',
      'host' => 'localhost',
      'port' => '',
      'driver' => 'mysql',
      'prefix' => '',
    ),
  ),
);

/**

```
using these commands we can enter into interactive shell and able to access the my sql DB:
```
python -c 'import pty; pty.spawn("/bin/sh")'

mysql -u dbuser -p

use drupaldb;

show tables;
```
