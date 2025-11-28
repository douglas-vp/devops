# Pré-requisitos para o Lab DevOps Automation

Este documento lista os pré-requisitos utilizados no curso **DevOps Automation**.  

Escolha o seu sistema operacional e siga o passo a passo correspondente para garantir que seu ambiente está pronto para os labs.

---

## 📚 Índice

1. [Ubuntu (nativo ou em VM)](#-se-você-está-usando-ubuntu-nativo-ou-em-vm)
2. [Windows com WSL 2 (recomendado)](#-se-você-está-usando-windows-com-wsl-2-recomendado)
3. [macOS](#-se-você-está-usando-macos)
4. [O que você poderá fazer ao final](#com-tudo-pronto)

---

## 🔧 Se você está usando **Ubuntu (nativo ou em VM)**

### 1. Atualize o sistema e instale ferramentas básicas

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y git curl unzip software-properties-common gnupg
```

### 2. Instale e configure o Git

```bash
sudo apt install git -y
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
git --version
```

### 3. Instale o Docker

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker $USER
newgrp docker
docker run hello-world
```

Documentação: [https://docs.docker.com/manuals](https://docs.docker.com/manuals)

### 4. Instale o AWS CLI

Você precisará baixar o pacote correto para a arquitetura do seu sistema.

**Para sistemas x86_64 (Intel/AMD):**

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

**Para sistemas ARM64:**

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-aarch64.zip" -o "awscliv2.zip"
```

Após baixar o arquivo correto para sua arquitetura:

```bash
unzip awscliv2.zip
sudo ./aws/install
aws --version
```

Documentação: [https://docs.aws.amazon.com/cli/](https://docs.aws.amazon.com/cli/)

### 5. Instale o Azure CLI

```bash
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
az version
```

Documentação: [https://learn.microsoft.com/en-us/cli/azure/?view=azure-cli-latest](https://learn.microsoft.com/en-us/cli/azure/?view=azure-cli-latest)

### 6. Instale o Terraform

```bash
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com noble main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

sudo apt update && sudo apt install terraform -y
terraform -version
```

Documentação: [https://developer.hashicorp.com/terraform/docs](https://developer.hashicorp.com/terraform/docs)

### 7. Instale o Ansible

```bash
sudo apt install ansible -y
ansible --version
```

Documentação: [https://docs.ansible.com/](https://docs.ansible.com/)

### 8. Instale o kubectl e o watch

Primeiro, obtenha a versão estável mais recente do `kubectl`:

```bash
KUBECTL_VERSION=$(curl -Ls https://dl.k8s.io/release/stable.txt)
echo "Versão estável do kubectl: $KUBECTL_VERSION"
```

**Para sistemas x86_64 (Intel/AMD):**

```bash
curl -LO "https://dl.k8s.io/release/$KUBECTL_VERSION/bin/linux/amd64/kubectl"
```

**Para sistemas ARM64:**

```bash
curl -LO "https://dl.k8s.io/release/$KUBECTL_VERSION/bin/linux/arm64/kubectl"
```

Instale o binário:

```bash
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
kubectl version --client
```

Instale o `watch`:

```bash
sudo apt install -y watch
watch --version
```

Documentação: [https://kubernetes.io/docs/home/](https://kubernetes.io/docs/home/)

### 9. Instale o Visual Studio Code

Baixe em: [https://code.visualstudio.com/](https://code.visualstudio.com/)

Instale as extensões recomendadas:

- Docker  
- Terraform  
- YAML  
- GitHub Pull Requests  

Documentação: [https://code.visualstudio.com/docs](https://code.visualstudio.com/docs)

---

## 💻 Se você está usando **Windows com WSL 2 (recomendado)**

### 1. Instale o WSL (Windows 11)

```powershell
wsl --install
```

> Isso instala o WSL 2 com Ubuntu automaticamente (no Windows 11).

### 2. Faça a configuração manual (se necessário)

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

Depois:

- Reinicie o computador  
- Baixe o kernel: [https://aka.ms/wsl2kernel](https://aka.ms/wsl2kernel)  
- Defina o WSL 2 como padrão:

```powershell
wsl --set-default-version 2
```

- Instale o Ubuntu pela Microsoft Store

### 3. Configure o ambiente dentro do Ubuntu (WSL)

Abra o Ubuntu (via WSL) e siga os mesmos passos da seção **Ubuntu (nativo ou em VM)** para instalar:

- Git  
- Docker  
- AWS CLI  
- Azure CLI  
- Terraform  
- Ansible  
- kubectl  
- VS Code (no Windows, com extensão Remote - WSL)  

### 4. Instale o Docker Desktop no Windows

Baixe em: [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)

> Durante a instalação, marque a opção para integração com WSL.

### 5. Instale o Visual Studio Code e a extensão **Remote - WSL**

Baixe o VS Code: [https://code.visualstudio.com/](https://code.visualstudio.com/)

No VS Code, instale a extensão:

- **Remote - WSL**

---

## 🍎 Se você está usando **macOS**

### 1. Instale o Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 2. Instale as ferramentas principais

```bash
brew install git terraform ansible node docker awscli azure-cli
```

### 3. Verifique as versões

```bash
git --version
terraform -version
ansible --version
docker --version
aws --version
az version
```

### 4. Instale o Docker Desktop

Baixe em: [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)

### 5. Instale o Visual Studio Code

Baixe em: [https://code.visualstudio.com/](https://code.visualstudio.com/)

### 6. Instale as extensões recomendadas

No VS Code, instale:

- Docker  
- Terraform  
- YAML  
- GitHub Pull Requests  
