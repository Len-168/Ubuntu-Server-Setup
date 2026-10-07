# 1. Security & System Fundamentals

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

```text

Ubuntu-Server-Setup/
│
├── initialize-server/
│   ├── 1-security-system-fundamentals.md
│   ├── 2-hostname-timezone-time.md
│   ├── 3-automatic-security-updates.md
│   ├── 4-firewall.md
│   ├── 5-system-verification.md
│   └── 6-reboot-verification.md
│
├── ssh/
│   ├── 1-bootstrap-ssh-access.md
│   ├── 2-setup-ssh-key.md
│   ├── 3-harden-sshd.md
│   └── 4-test-ssh-access.md
│
├── docker/
├── monitoring/
├── backup/
└── production-checklist.md

```