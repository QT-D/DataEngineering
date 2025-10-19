# 1. Remove old versions (if any)
sudo apt remove docker docker-engine docker.io containerd runc

# 2. Update packages
sudo apt update

# 3. Install dependencies
sudo apt install -y ca-certificates curl gnupg lsb-release

# 4. Add Docker’s official GPG key
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

# 5. Add Docker repo
echo \
  "deb [arch=$(dpkg --print-architecture) \
  signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# 6. Install Docker Engine
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# 7. Verify
sudo docker --version
sudo docker run hello-world

