## Objective

Retrieve the password in a file named `readme` found in the `homedirectory` but connecting via `SSH` will automatically logged you out due to modified `.bashrc`.

## Method

### 1. Connect to the server using `ssh`

I connect to the server normally using `ssh` and the default host and port, but it doesn't help retrieve the password because of the modified `bashrc` and the session closes.

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220
```

- `ssh` used to securely log onto the remote system.  
- `-p` port to connect to on the remote host.

### 2. Print the `readme` file

The important technique is running `cat readme` as part of the `ssh` command. This executes the command on the remote host without relying on an interactive login shell that triggers the logout behavior.

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```

- `cat` Prints the contents of a file to standard output (stdout).

## Key Takeaway

- **SSH remote commands:** Execute a command on a remote host by appending it to the `ssh` command.
- **Non-interactive execution:** Running a remote command can retrieve its output without opening an interactive shell session.
- **Troubleshooting:** When an interactive login fails, consider whether executing a command directly over SSH can accomplish the task.


## References

- [Official OverTheWire Bandit](https://overthewire.org/wargames/bandit/)
- `man ssh` SSH client manual page