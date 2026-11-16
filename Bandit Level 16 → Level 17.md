## Objective

Find the service listening on ports 31000 - 32000 that uses SSL/TLS and provides the credentials needed to access the next level.
## Method

### 1. Scan the port range

I used Nmap to scan the specified port range on localhost and attempt to identify the services running on the discovered ports.

```bash
nmap -sV -p 31000-32000 localhost
```

-  `-p 31000-32000` specifies the port range to scan.
- `-sV` attempts to identify the services and their versions.

### 2. Connect to the correct service

After identifying the appropriate service, I connected to it using an SSL/TLS client and submitted the current level's password. The service returned a private SSH key.

### 3. Secure the private key

I restricted access to the private key file before using it for SSH auth.

```
sudo chmod g-rx,o-rx bandit17.pass
```
- `g-rx` removes read and execute permissions from the group.
- `o-rx` removes read and execute permissions from other users.
- `sudo` runs the command with elevated privileges.
This gives the file owner read/write permission and removes all permissions for group and other users.

### 4. Connect to the next level

I used the private key to authenticate to Bandit Level 17.

```
ssh bandit17@bandit.labs.overthewire.org -p 2220 -i bandit17.pass
```
- `-p 2220` specifies the SSH port.
- `-i` bandit17.pass specifies the private key file to use for auth.

The filename `bandit17.pass` is the name I chose for my local file. You can use a different filename as long as you specify the correct path.
## Key Takeaway

- **Nmap:** Scan a specified port range to discover accessible services.
- **Service detection:** Use `-sV` to attempt to identify services and versions.
- **SSL/TLS:** Use an appropriate client to communicate with a TLS-enabled service.
- **SSH authentication:** A private key can authenticate a user when the server accepts the corresponding key.
- **File permissions:** Use `chmod 600` to restrict access to a private key file.
## References

- [Official OverTheWire Bandit](https://overthewire.org/wargames/bandit/)
- `man nmap` — Nmap manual page
- `man openssl` — OpenSSL manual page
- `man ssh` — SSH client manual page
- `man chmod` — File permissions manual page