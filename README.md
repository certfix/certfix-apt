# Certfix APT Repository

This is the official APT package distribution repository for the [Certfix Agent](https://github.com/certfix/certfix-agent). It is served via GitHub Pages and contains only compiled `.deb` packages.

> **Do not clone this repository.** To install the agent, follow the APT instructions below.

## Installation

To install the Certfix Agent on Debian/Ubuntu systems:

### 1. Add the GPG Key
```bash
curl -fsSL https://certfix.github.io/certfix-apt/certfix-agent.gpg | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/certfix-agent.gpg
```

### 2. Add the Repository
```bash
echo "deb [arch=amd64,arm64] https://certfix.github.io/certfix-apt stable main" | sudo tee /etc/apt/sources.list.d/certfix.list
```

### 3. Install the Agent
```bash
sudo apt update
sudo apt install certfix-agent
```

## Configuration

After installation, the agent needs to be configured to connect to the Certfix API.

### Option A: Configuration File
Create `/etc/certfix-agent/config.json`:
```json
{
  "token": "YOUR_SERVICE_KEY",
  "endpoint": "http://<your-certfix-core-host>:9976"
}
```

### Option B: Environment Variables
Edit `/etc/default/certfix-agent`:
```bash
CERTFIX_AGENT_TOKEN="YOUR_SERVICE_KEY"
CERTFIX_AGENT_ENDPOINT="http://<your-certfix-core-host>:9976"
```

After configuring, start the service:
```bash
sudo systemctl enable --now certfix-agent
```

## Supported Architectures

- `amd64` (x86_64)
- `arm64` (ARMv8)

## License

MIT
