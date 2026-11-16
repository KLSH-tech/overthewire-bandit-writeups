## Objective

Find the only line that differs between `password.old` and `password.new` to obtain the next level's password.
## Method

I used `diff` to compare files (lists changes to turn old_file into new_file)

```bash
diff passwords.old passwords.new
```

The command displays the lines that differ between the two files. The changed line in passwords.new contains the next level's password
## Key Takeaway

- **diff:** Compare files line by line and displays their differences.
- **Practical use:** Useful for identifying changes between versions of files.

## References

- [Official OverTheWire Bandit](https://overthewire.org/wargames/bandit/)
-  `man diff` - Full manual
- `tldr diff` - Quick command examples