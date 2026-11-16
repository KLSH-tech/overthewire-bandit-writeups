## Objective

Use the provided `setuid` binary  in the home directory to retrieve the password for the next level.
## Method

### 1. Execute the provided binary

I initially tried running `bandit20-do` directly, but the command needed `./` to specify that the executable was in the current directory.

```bash
./bandit20-do whoami
```

- `./` Specifies the current directory.
- `whoami` Displays the username associated with the command's execution context.

### 2. Retrieve the next level's password

I used the provided binary to execute cat on the password file for the next level.

```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

- `cat` Prints the contents of a file to standard output (stdout).
- `bandit20-do` The provided `setuid` binary that executes a command with the privileges of the `bandit20` user.

## Key Takeaway

- **Current directory execution:** Use `./program` to execute a program located in the current directory.
- **Setuid binaries:** A `setuid` executable can run with the privileges of its owning user.
- **Privilege escalation:** The provided `bandit20-do` binary allows commands to run with `bandit20` privileges, enabling access to the next level's password.


## References

- [Official OverTheWire Bandit](https://overthewire.org/wargames/bandit/)
    
- `man [command]` — [Manual page for the command]