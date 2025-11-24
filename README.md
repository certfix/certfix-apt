# Certfix APT Repository

This is the official APT repository for the [Certfix Agent](https://github.com/certfix/certfix-agent).

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
  "token": "YOUR_API_TOKEN",
  "endpoint": "https://api.certfix.io"
}
```

### Option B: Environment Variables
Edit `/etc/default/certfix-agent`:
```bash
CERTFIX_AGENT_TOKEN="YOUR_API_TOKEN"
CERTFIX_AGENT_ENDPOINT="https://api.certfix.io"
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
