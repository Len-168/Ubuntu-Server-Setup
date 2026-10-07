## 1. Install cloudflared on Ubuntu
For your setup, ` I recommend running cloudflared directly on Ubuntu as a systemd service`, rather `than inside Docker`.
That way remote administration of the machine does not depend on your Docker stack being healthy.

1.1. Install Cloudflare's repository

```bash
sudo mkdir -p --mode=0755 /usr/share/keyrings
```

```bash
curl -fsSL https://pkg.cloudflare.com/cloudflare-main.gpg \
  | sudo tee /usr/share/keyrings/cloudflare-main.gpg >/dev/null
```

1.2. Add the repository

```bash
echo "deb [signed-by=/usr/share/keyrings/cloudflare-main.gpg] https://pkg.cloudflare.com/cloudflared any main" \
  | sudo tee /etc/apt/sources.list.d/cloudflared.list
```

1.3. Install cloudflared

```bash
sudo apt install -y cloudflared
```

1.4. Verify
```bash
cloudflared --version
```

## 2. Configure Cloudflare Access first
This step is important.
Do this `before publishing the SSH hostname.`

2.1. Go to Cloudflare:

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

2.2. Destinations

Entry hostname
```text
Add subdomain + domain

# Example
ssh.YOUR-DOMAIN.com

```

2.3. Create a policy like:

```text
Policy name: Home Lab Admin

Action: Allow

Include: Emails

Value:
your-email@example.com

# Then Save policy
```