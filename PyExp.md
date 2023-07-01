
# Nmap scan

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/cc2c53ad-25fa-49ab-aeb6-4fc34a8b2a52)


# Hydra DB auth Bruteforce

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/5d456f10-fb36-46a2-8b11-cb9ec6838271)

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/67459747-1f65-44a9-bd53-1c6bc3232398)

- there is a SSH port at 1337 tried the same username and password creds , but not able to access it.

# Entering into SQL DB

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/e0036795-eb7c-4592-a9e1-7f0fc343f948)

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/e85c6e8e-26e4-4309-9da1-cb2509b12bde)

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/a88884e5-71cd-4c01-a526-3340029fde64)

- We got the cred and key, now we can use decoder to decode fernet key.it may be a ssh user and pass

# Decoding Key

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/26aa6e3f-d204-406e-81a5-fa6b7b78e20a)

# SSH into user 

- Found the user flag
- Searching for anyother root process using `sudo -l`

  ![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/de6e701d-ba6a-47b8-93b7-9ec3c0546cdd)


# Root Shell 

- After a long tries, finally got the root shell via user-space importing `__import__`.

`__import__('os').system('sudo /bin/bash')`

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/f5a28267-5a2f-471d-ad5a-2479d1ce38ae)

![image](https://github.com/shyamprasath18/offsec-labs/assets/66670617/04af50f7-3224-40e8-bf34-c0b07e30113f)

