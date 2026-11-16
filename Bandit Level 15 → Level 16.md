## Objective

Submit the current level's password to the specified localhost port using an SSL/TLS-encrypted connection to retrieve the next level's password.

## Method

### 1. Establish an SSL/TLS connection

I used `openssl s_client` to establish an interactive TLS connection to the service running on `localhost`.

```bash
openssl s_client -connect localhost:30001 -quiet
```

- `s_client` starts an SSL/TLS client for testing and communicating with TLS-enabled services.
- `-connect localhost:30001` specifies the destination host and port.
- `-quiet` suppresses certain connection information and implicitly enables `-ign_eof` and `-nocommands`.


### 2. Submit the current password

After the connection was established, I pasted the current level's password into the interactive session and pressed Enter. The service returned the password for the next level.

## Key Takeaway

- **OpenSSL:** `openssl s_client` can establish and interact with an SSL/TLS connection.
- **Command-line options:** Options can implicitly enable other options, so reading the manual helps explain their combined behavior.
- **Troubleshooting:** A blank terminal line does not necessarily mean a connection has failed. Understand the program's input and connection behavior before interrupting it.


## References

- [Official OverTheWire Bandit](https://overthewire.org/wargames/bandit/)
- `man s_client` — OpenSSL client manual page