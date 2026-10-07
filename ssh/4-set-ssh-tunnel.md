## 1. Install cloudflared on Ubuntu
For your setup, ` I recommend running cloudflared directly on Ubuntu as a systemd service`, rather `than inside Docker`.
That way remote administration of the machine does not depend on your Docker stack being healthy.

Install Cloudflare's repository

```bash
sudo mkdir -p --mode=0755 /usr/share/keyrings
```

```bash
curl -fsSL https://pkg.cloudflare.com/cloudflare-main.gpg \
  | sudo tee /usr/share/keyrings/cloudflare-main.gpg >/dev/null
```

Add the repository

```bash
echo "deb [signed-by=/usr/share/keyrings/cloudflare-main.gpg] https://pkg.cloudflare.com/cloudflared any main" \
  | sudo tee /etc/apt/sources.list.d/cloudflared.list
```

Install cloudflared
```bash

sudo apt install -y cloudflared
```

Verify
```bash
cloudflared --version
```

## 2. Configure Cloudflare Access first
This step is important.
Do this `before publishing the SSH hostname.`

Go to Cloudflare:

```text
Zero Trust
   ↓
Access controls
   ↓
Applications
   ↓
Create new application
   ↓
Self-hosted and private
   ↓
Add public hostname
```