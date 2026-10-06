# 1. Generate an SSH key on your local computer
On Windows PowerShell, Linux, or macOS:
```bash
ssh-keygen -t ed25519
```
You will see:
```text
Enter file in which to save the key: ~/.ssh/id_ed25519
```
Press Enter twice to finish.

Default location:
```text
# Windows
C:\Users\YOUR_USERNAME\.ssh\id_ed25519

# Linux/Mac
~/.ssh/id_ed25519
```
You will have two files:
```text
# Private key (keep secret) (Never copy or share)
~/.ssh/id_ed25519

# Public key (share this one to server)
~/.ssh/id_ed25519.pub
```

# 2. Copy the SSH public key to Server

## Method 1

1. If your local machine is Linux/macOS:
```bash
ssh-copy-id dev@[IP_ADDRESS]
```
Then enter the Ubuntu password one final time.


2. On Windows, `ssh-copy-id` often isn't installed. You can run:
```bash
type $env:USERPROFILE\.ssh\id_ed25519.pub | ssh dev@[IP_ADDRESS] "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
```
Enter your Ubuntu password.

**Optional: Test ssh-copy-id:**
```bash
ssh dev@[IP_ADDRESS]
```
You should now login without password.
