# Guia de Primeiros Passos na AWS 🌩️

Este README foi pensado para **qualquer pessoa**, mesmo sem experiência prévia em nuvem, conseguir:

- Criar uma conta na AWS  
- Proteger a conta (root + IAM + MFA)  
- Criar uma máquina virtual (EC2) com script de inicialização (User Data)  
- Acessar a máquina via SSH  
- Encerrar recursos para evitar custos  
- Criar uma VPC básica com sub-redes públicas e privadas  

---

## 📚 Índice

1. [Pré-requisitos](#-pré-requisitos)  
2. [Criar sua conta na AWS](#1-criar-sua-conta-na-aws)  
3. [Conhecer o Console da AWS](#2-conhecer-o-console-da-aws)  
4. [Segurança básica: root, IAM e MFA](#3-segurança-básica-root-iam-e-mfa)  
   - [3.1. Entendendo o usuário root](#31-entendendo-o-usuário-root)  
   - [3.2. Ativar MFA no usuário root](#32-ativar-mfa-no-usuário-root)  
   - [3.3. Criar um usuário administrador IAM](#33-criar-um-usuário-administrador-iam)  
5. [Criar sua primeira instância EC2](#4-criar-sua-primeira-instância-ec2)  
   - [4.1. Criar um par de chaves (Key Pair)](#41-criar-um-par-de-chaves-key-pair)  
   - [4.2. Configurar e lançar a instância](#42-configurar-e-lançar-a-instância)  
   - [4.3. Automatizar a configuração com User Data](#43-automatizar-a-configuração-com-user-data)  
6. [Acessar a instância via SSH](#5-acessar-a-instância-via-ssh)  
7. [Testar o servidor web (Nginx)](#6-testar-o-servidor-web-nginx)  
8. [Encerrar a instância e limpar recursos](#7-encerrar-a-instância-e-limpar-recursos)  
9. [Criar uma VPC básica](#8-criar-uma-vpc-básica)  
10. [O que você já consegue fazer](#9-o-que-você-já-consegue-fazer)  
11. [Próximos passos sugeridos](#10-próximos-passos-sugeridos)  

---

## ✅ Pré-requisitos

- Navegador web (Chrome, Firefox, Edge etc.).  
- Um e-mail que você acesse com frequência.  
- Cartão de crédito para cadastro na AWS (necessário, mesmo para o Free Tier).  
- (Opcional, mas recomendado)  
  - Terminal Linux/macOS **ou**  
  - Windows com **WSL** ou outro cliente SSH.  

---

## 1. Criar sua conta na AWS

1. Abra o navegador e acesse o Google.  
2. Pesquise por: **\`criar conta AWS\`**.  
3. Clique no resultado oficial da **Amazon Web Services**.  
4. Na página de criação de conta:  
   - Informe um **e-mail válido**.  
   - Crie uma **senha forte**.  
   - Preencha seus dados pessoais/empresa.  
   - Cadastre um **cartão de crédito**.  
   - Confirme o **código enviado por e-mail/SMS**, se solicitado.  
5. Conclua o cadastro até aparecer que sua conta está ativa.  

> A interface da AWS pode mudar com o tempo, mas o fluxo geral de criação de conta permanece semelhante.

---

## 2. Conhecer o Console da AWS

1. Acesse: **https://console.aws.amazon.com**  
2. Faça login com seu e-mail e senha cadastrados.  
3. Você verá o **AWS Management Console**, o painel central da nuvem.  

Principais pontos do console:

- **Barra de busca** no topo: use para procurar serviços como `EC2`, `S3`, `IAM`, `VPC` etc.  
- Área de **serviços recentes**.  
- Acesso ao painel de **faturamento (Billing)**.  

👉 **Dica:** acostume-se a usar a **barra de busca**. Ela é seu melhor amigo na AWS.

---

## 3. Segurança básica: root, IAM e MFA

### 3.1. Entendendo o usuário root

- O usuário **root** é o dono da conta.  
- Tem acesso completo a **tudo** na AWS.  
- Se alguém roubar essa senha, essa pessoa controla a conta inteira:  
  - Pode apagar dados, backups, recursos;  
  - Pode gerar gastos altos.  

**Boa prática:**

- Use o root **apenas** para:  
  - Configurações iniciais,  
  - Faturamento,  
  - Criação do primeiro usuário administrador.  
- Depois disso, **não use mais o root no dia a dia**.  

---

### 3.2. Ativar MFA no usuário root

MFA (Multi-Factor Authentication) adiciona uma segunda etapa de segurança (código no celular).

Passo a passo:

1. Logado como **root**, clique no seu nome (canto superior direito) e vá em  
   **“Security credentials”** (Credenciais de segurança).  
2. Encontre a seção de **MFA**.  
3. Clique em **“Ativar/Configurar MFA”**.  
4. No seu celular, instale um app de autenticação (ex.: *Microsoft Authenticator* ou *Google Authenticator*).  
5. Na AWS, escolha o tipo de MFA com app de autenticação.  
6. Escaneie o **QR Code** com o app.  
7. Informe na AWS **dois códigos** seguidos gerados pelo app.  
8. Confirme.  

Pronto: o usuário root agora exige senha **+ código do app**.

---

### 3.3. Criar um usuário administrador IAM

Agora vamos criar um usuário para uso diário, no lugar do root.

1. No console, procure por **\`IAM\`** na barra de busca.  
2. Clique em **IAM**.  
3. No menu lateral, clique em **Users (Usuários)**.  
4. Clique em **Add user** (Adicionar usuário).  
5. Defina um nome, por exemplo: `adm-user` ou `devops-admin`.  
6. Marque a opção para acesso ao **AWS Management Console**.  
7. Defina a senha:  
   - Gerada automaticamente **ou**  
   - Definida manualmente.  
8. (Opcional) Exigir troca de senha no primeiro login.  

#### Conceder permissão de administrador

1. Ainda na criação do usuário, escolha **Add user to group**.  
2. Crie um grupo chamado, por exemplo, `Admins`.  
3. Procure pela política **\`AdministratorAccess\`**.  
4. Selecione essa política e associe ao grupo `Admins`.  
5. Adicione o usuário (`adm-user`) a esse grupo.  

Ao final, a AWS mostrará:

- A URL de login de usuários IAM,  
- O nome de usuário,  
- E (se escolhido) um arquivo CSV com as credenciais.  

> **Importante:** se não salvar a senha/CSV nesse momento, não será possível visualizá-la depois.  
> Se perder, será necessário redefinir a senha via IAM.

---

## 4. Criar sua primeira instância EC2

### 4.1. Criar um par de chaves (Key Pair)

Esse par de chaves será usado para se conectar via SSH.

1. No console, use a barra de busca e procure por **\`EC2\`**.  
2. Entre em **EC2**.  
3. No menu lateral, clique em **Key pairs**.  
4. Clique em **Create key pair**.  
5. Dê um nome, por exemplo: `devops-automation-01`.  
6. Se estiver em Linux/macOS, escolha o tipo de arquivo **\`.pem\`**.  
7. Clique em **Create**.  

Um arquivo `devops-automation-01.pem` será baixado para o seu computador.

---

### 4.2. Configurar e lançar a instância

1. Ainda em EC2, vá em **Instances**.  
2. Clique em **Launch instances**.  
3. Em **Name**, use algo como: `DevOps-Automation-VM`.  

#### Sistema operacional (AMI)

4. Em **Application and OS Images (AMI)**:  
   - Selecione uma imagem do tipo **Ubuntu Server** (por exemplo, Ubuntu 22.04 LTS).  

#### Tipo de instância

5. Em **Instance type**:  
   - Selecione **\`t2.micro\`** (elegível ao Free Tier na maioria dos casos).  

#### Par de chaves

6. Em **Key pair (login)**:  
   - Selecione o par de chaves criado anteriormente (`devops-automation-01`).  

#### Rede

7. Em **Network settings**:  
   - Use a **VPC padrão** (default VPC), se estiver disponível.  
   - Certifique-se que **Auto-assign public IP** está **Enabled** (para ter IP público).  

#### Security Group (Firewall)

8. Crie um novo **Security Group**, por exemplo: `sg-devops-automation`.  
9. Adicione as regras de **Inbound**:  
   - **SSH** – Porta `22` – Origem: de preferência **My IP**, ou `0.0.0.0/0` (qualquer lugar).  
   - **HTTP** – Porta `80` – Origem: `0.0.0.0/0`.  
   - **HTTPS** – Porta `443` – Origem: `0.0.0.0/0`.  

#### Armazenamento

10. Em **Storage**, mantenha o tamanho padrão (por exemplo, **8 GB gp3**).  

---

### 4.3. Automatizar a configuração com User Data

User Data é um script que roda automaticamente na **primeira inicialização** da instância.

1. Na tela de configuração avançada, procure por **Advanced details**.  
2. Localize o campo **User data**.  
3. Cole o script abaixo:

```bash
#!/bin/bash
apt update -y
apt upgrade -y
apt install -y nginx
echo "Servidor Ubuntu com Nginx via User Data" > /var/www/html/index.html
systemctl enable nginx
systemctl start nginx
```

Esse script irá:

- Atualizar o sistema (`apt update` e `apt upgrade`);  
- Instalar o **Nginx**;  
- Criar uma página simples em `/var/www/html/index.html`;  
- Habilitar e iniciar o serviço **Nginx**.  

4. Clique em **Launch instance** para criar a máquina.  

#### Acompanhar a criação

- Vá em **Instances**.  
- Aguarde o **Status** ficar como `running`.  
- Aguarde os dois **Status checks** ficarem ok.  
- Anote o **Public IPv4 address** (IP público) e/ou o **Public DNS**.  

---

## 5. Acessar a instância via SSH

No computador local (Linux/macOS ou WSL):

1. Vá até o diretório dos downloads:

```bash
cd ~/Downloads
```

2. Dê permissão correta para a chave:

```bash
chmod 400 devops-automation-01.pem
```

3. Conecte na instância (substitua `SEU_IP_PUBLICO` pelo IP anotado):

```bash
ssh -i devops-automation-01.pem ubuntu@SEU_IP_PUBLICO
```

- Na primeira vez, confirme com `yes` ao ser perguntado sobre a autenticidade do host.  
- Se tudo deu certo, você estará logado dentro da máquina virtual na AWS.  

---

## 6. Testar o servidor web (Nginx)

### 6.1. Verificar o arquivo criado pelo User Data

Dentro da instância, rode:

```bash
cat /var/www/html/index.html
```

Você deverá ver algo como:

```text
Servidor Ubuntu com Nginx via User Data
```

### 6.2. Testar no navegador

No seu navegador, acesse:

```text
http://SEU_IP_PUBLICO
```

Você deverá ver a página do Nginx (ou a mensagem configurada, dependendo da personalização).

Se aparecer, significa que:

- A instância está online,  
- O Security Group está liberando porta 80,  
- O **User Data** foi executado corretamente.  

---

## 7. Encerrar a instância e limpar recursos

Para evitar custos desnecessários:

1. No console da AWS, vá em **EC2 > Instances**.  
2. Selecione sua instância.  
3. Clique em **Instance state > Terminate instance**.  
4. Confirme.  

Depois disso, você pode:

- Remover o **Security Group** criado, caso não vá reutilizar.  
- Remover o **Key pair**, se não for mais necessário.  

> A AWS pode cobrar por recursos que continuem ativos (instâncias, discos, IPs elásticos, etc.), portanto sempre revise o que está em uso.

---

## 8. Criar uma VPC básica

A **VPC (Virtual Private Cloud)** é sua rede privada na AWS.

### Conceitos rápidos

- **VPC**: bloco de rede, por exemplo `10.0.0.0/16`.  
- **Subnet**: sub-redes dentro da VPC (`10.0.1.0/24`, `10.0.2.0/24` etc.).  
  - **Pública**: com rota para a internet (via **Internet Gateway**).  
  - **Privada**: sem acesso direto à internet.  
- **Route Table**: define para onde o tráfego vai.  
- **Internet Gateway (IGW)**: faz a ponte da VPC com a internet.  

### Criando uma VPC com sub-redes públicas e privadas

1. No console, procure por **\`VPC\`**.  
2. Clique em **VPC**.  
3. Use a opção de criação pelo assistente (por exemplo, **“VPC and more”**).  
4. Defina:  
   - Nome: `VPC-DevOps`.  
   - Bloco CIDR da VPC: `10.0.0.0/16` (exemplo).  
   - Número de **Availability Zones**: por exemplo, `3`.  
   - Número de **public subnets**: `3`.  
   - Número de **private subnets**: `3`.  
5. Habilite:  
   - **DNS resolution**,  
   - **DNS hostnames**.  
6. Confirme a criação.  

O assistente criará automaticamente:

- A **VPC**,  
- **Subnets públicas e privadas**,  
- **Internet Gateway** e associação com a VPC,  
- **Route tables** com rotas adequadas:  
  - Subnets públicas com rota `0.0.0.0/0 → IGW`,  
  - Subnets privadas sem rota direta para a internet (podem usar NAT, se configurado no futuro).  

---

## 9. O que você já consegue fazer

Após seguir este README, você está apto a:

- Criar e proteger uma conta AWS (root + MFA + IAM Admin).  
- Navegar pelo console da AWS com segurança.  
- Criar e configurar uma instância EC2 com:  
  - **Key Pair**,  
  - **Security Group**,  
  - **IP público**,  
  - **Script de User Data**.  
- Conectar via SSH na instância.  
- Subir um servidor web simples (Nginx) automaticamente.  
- Encerrar recursos e evitar custos.  
- Entender e criar uma **VPC básica** com sub-redes públicas e privadas.  

---

## 10. Próximos passos sugeridos

Para continuar evoluindo na AWS e em DevOps:

- Criar **instâncias adicionais** em subnets **privadas** acessando-as via **bastion host**.  
- Aprender sobre:  
  - **S3** (armazenamento de objetos),  
  - **RDS** (banco de dados gerenciado),  
  - **IAM Roles** e políticas mais específicas (princípio do menor privilégio),  
  - **CloudWatch** (logs e monitoramento),  
  - **Auto Scaling Groups** e **Load Balancers**.  
- Integrar esse ambiente com ferramentas DevOps como:  
  - **Git/GitHub**,  
  - **Ansible**,  
  - **Docker**,  
  - **Jenkins/GitHub Actions**,  
  - **Terraform** (para infra como código).  