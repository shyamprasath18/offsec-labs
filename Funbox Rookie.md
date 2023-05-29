
## Nmap scan

```
PORT   STATE SERVICE REASON  VERSION
21/tcp open  ftp     syn-ack ProFTPD 1.3.5e
22/tcp open  ssh     syn-ack OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 f9467dfe0c4da97e2d77740fa2517251 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDMD7EHN/CpFOxv4hW16hSiL9/hrqfgN7N5gfqvnRwCeDJ8jj4kzV9XNVm/NN3u+fE7zrclQWDtGRu4oryuQv+25XjPJG7z+OdJ6ncD8k/VyHm3ncPIt1skZNTe8WGR9BGHf2dSvyEgW6Iu2TqICR+Vak48KdMIbmjCo8jbiAx4pNvUjkv7z+vzmr3wJakRhiIa2aA7TFeAVe5o9/Se6IOc/I4ByXcarmeU6hOytDb8qmUSYxSV1nea1jYKinXgCZ7MpAoFB8qPtiy4wryzBgssjAiqAFPEmPjaU96hDAsGMeQ0yFLeCoDTxeY8xnc+oWjU/mm1ISbiJ/IqX2N81xtP
|   256 15004667809b40123a0c6607db1d1847 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBHG2MCQtlbU+bwb4Cuz2xWoPH4/WBRJtUP5pDp8LQM175mj/IP9ORztHIBB+dyfrCshyxnFcIFc35MXp2qhgJFM=
|   256 75ba6695bb0f16de7e7ea17b273bb058 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIFhzTG7CoqPllLoboDB4lTrHUfFJLHbEWIRUP1lMA4rT
80/tcp open  http    syn-ack Apache httpd 2.4.29 ((Ubuntu))
| http-robots.txt: 1 disallowed entry 
|_/logs/
| http-methods: 
|_  Supported Methods: GET POST OPTIONS HEAD
|_http-title: Apache2 Ubuntu Default Page: It works
|_http-server-header: Apache/2.4.29 (Ubuntu)
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

```

## Ftp enumeration

- Found some zip files. one `.@admins` file is there
```
SGkgQWRtaW5zLAoKYmUgY2FyZWZ1bGwgd2l0aCB5b3VyIGtleXMuIEZpbmQgdGhlbSBpbiAleW91cm5hbWUlLnppcC4KVGhlIHBhc3N3b3JkcyBhcmUgdGhlIG9sZCBvbmVzLgoKUmVnYXJkcwpyb290
```
![Pasted image 20230529101945](https://github.com/shyamprasath18/offsec-labs/assets/66670617/3b3717e5-ad30-401a-b9c7-aba10bf028ad)


## cracking zip

![Pasted image 20230529104455](https://github.com/shyamprasath18/offsec-labs/assets/66670617/668e99df-62fa-496c-857c-b1cf5ad63de9)


![Pasted image 20230529105056](https://github.com/shyamprasath18/offsec-labs/assets/66670617/4cd67a09-fcbb-4d30-8269-ef66af9a65e3)


## Trying to SSH

![Pasted image 20230529105005](https://github.com/shyamprasath18/offsec-labs/assets/66670617/9ab30145-f196-4240-9f76-8abcad74b715)


![Pasted image 20230529105200](https://github.com/shyamprasath18/offsec-labs/assets/66670617/a0b5af24-eec4-4a68-b77d-9de56543a6d9)


- `rbash` shell is there.

![Pasted image 20230529105323](https://github.com/shyamprasath18/offsec-labs/assets/66670617/c7c91940-3ef0-4f69-9f5c-743579979272)


## Root privilage

- there is a .mysql_history file, the tom to root password is `xx11yy22!`.

![Pasted image 20230529105550](https://github.com/shyamprasath18/offsec-labs/assets/66670617/ceefd534-a934-4b72-a0d7-7665b71c11a0)


