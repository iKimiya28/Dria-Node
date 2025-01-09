# Dria Node Setup Guide

A comprehensive guide to installing and managing your Dria node efficiently. Follow the steps below to ensure a smooth setup.

---

## Official Resources
- **Official Website for More Guides**: [https://dria.co/join](https://dria.co/join)  
- **Check Leaderboard**: [https://steps.leaderboard.dria.co/](https://steps.leaderboard.dria.co/)

---

## 1. Install Dependencies

### Install Docker
Run the following commands to install Docker and its required dependencies:

```bash
# Update and upgrade system packages
sudo apt update -y && sudo apt upgrade -y

# Remove conflicting packages
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

# Install Docker prerequisites
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add Docker's official repository
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker
sudo apt update -y && sudo apt upgrade -y
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Set permissions for Docker Compose
sudo chmod +x /usr/local/bin/docker-compose

# Verify Docker installation
docker --version
```

### Install Ollama
To install Ollama, run:
```bash
curl -fsSL https://ollama.com/install.sh | sh
```

---

## 2. Install Dria Node

Follow these steps to download and prepare the Dria Node:

```bash
# Navigate to home directory
cd $HOME

# Download the Dria Node launcher
curl -L -o dkn-compute-node.zip https://github.com/firstbatchxyz/dkn-compute-launcher/releases/latest/download/dkn-compute-launcher-linux-amd64.zip

# Extract the downloaded files
unzip dkn-compute-node.zip

# Navigate into the extracted directory
cd dkn-compute-node
```

---

## 3. Run Dria Node

Start the Dria Node with the following command:
```bash
./dkn-compute-launcher
```

### Notes:
1. **DKN Wallet**: Enter Metamask Private Key without the `0x` prefix.
2. **Model Selection**:  
   - The higher the model, the more points you earn. Select a model based on your VPS resources.  
   - Example: `"qwen 2.5-coder:1.5b"` is suitable for most VPS systems. Ensure other processes are stopped to free resources if needed.  
   - **Important**: Models are downloaded during selection, so selecting too many models will require significant disk space and bandwidth.  
3. **API-Only Models**: For models that work with APIs and do not consume VPS resources, get free or paid API keys:  
   - [Gemini API](https://aistudio.google.com/app/apikey)  
   - [Open Router API](https://openrouter.ai/settings/keys)  
   - [OpenAI API (Paid)](https://platform.openai.com/api-keys)  
4. **Optional APIs**: For Jina and Serper, you can skip them by pressing `Enter`, or obtain their APIs for added functionality.  

Once the setup is complete, the node will verify your hardware requirements. This process may take a few minutes.

### Running Node on Screen
To keep your node running in the background:
```bash
screen -S dkn
./dkn-compute-launcher
```

---

## Additional Information
- **Earn the Node-Keeper Role**: Join the Dria Discord community and claim your **Node-Keeper** role after successfully setting up your node.
- **Check Leaderboard**: [https://steps.leaderboard.dria.co/](https://steps.leaderboard.dria.co/)
