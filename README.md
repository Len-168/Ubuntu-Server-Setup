# 1 - Generate an SSH key on your local computer
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
# Private key (keep secret)
~/.ssh/id_ed25519

# Public key (share this one to server)
~/.ssh/id_ed25519.pub
```
