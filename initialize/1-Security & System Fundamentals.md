# 1. Phase 1: Security & System Fundamentals

1.1. Update and Upgrade: Ensure you have the latest security patches before continuing.

```bash
sudo apt update && sudo apt upgrade -y
sudo apt autoremove -y
```

1.2. Create a New Sudo User: Avoid using the root account for daily tasks.

```bash
# Create a new user
sudo adduser your_username

# Add user to the sudo group
sudo usermod -aG sudo your_username

# (Optional) Check user has sudo or not:
groups your_username # should return [your_username: your_username sudo]
```
1.3. Setup SSH Key-based Authentication: