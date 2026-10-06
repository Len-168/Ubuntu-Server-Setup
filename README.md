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

## Method 1 : The Automated One-Liner

**1. If your local machine is Linux/macOS:**
```bash
ssh-copy-id dev@[IP_ADDRESS]
```
Then enter the Ubuntu password one final time.


**2. On Windows, `ssh-copy-id` often isn't installed. You can run:**
```powershell
type $env:USERPROFILE\.ssh\id_ed25519.pub | ssh dev@[IP_ADDRESS] "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
```
Enter your Ubuntu password.


## Method 2: The Manual Copy-Paste

**1. Local machine (Linux/macOS):**

```bash
cat ~/.ssh/id_ed25519.pub
```

**2. Local machine (Windows):**
```powershell
type $env:USERPROFILE\.ssh\id_ed25519.pub
```

It will look similar to:
```text
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAA... yourpc
```


On Ubuntu: 
```bash
mkdir -p ~/.ssh
nano ~/.ssh/authorized_keys
```

Paste the public key.

Then save and exit. (Ctrl + O, Enter, Ctrl + X)

Then fix permissions:
```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```
