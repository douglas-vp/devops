# Guia de Primeiros Passos no Azure ☁️

Este README foi pensado para qualquer pessoa, mesmo sem experiência prévia em nuvem, conseguir:

- Criar uma **conta gratuita** no Azure
- Entender a **interface do portal**
- Compreender e criar um **Resource Group**
- Criar uma **máquina virtual (VM)** via portal
- Acessar a VM via **SSH**
- Criar um **Storage Account** e um **container**
- Deletar tudo de forma organizada para não gerar custos desnecessários

**Obs: É extremamente importante consultar a documentação oficial**

---

## 📚 Índice

1. [Conta gratuita no Azure](#1-conta-gratuita-no-azure)  
2. [Conhecendo o portal do Azure](#2-conhecendo-o-portal-do-azure)  
3. [Resource Group: a “caixa organizadora”](#3-resource-group-a-caixa-organizadora)  
   - [3.1. Conceito](#31-conceito)  
   - [3.2. Criando um Resource Group](#32-criando-um-resource-group)  
4. [Usando o Cloud Shell do Azure](#4-usando-o-cloud-shell-do-azure)  
5. [Criando sua primeira Máquina Virtual (VM)](#5-criando-sua-primeira-máquina-virtual-vm)  
   - [5.1. Acessar a tela de criação](#51-acessar-a-tela-de-criação)  
   - [5.2. Usando o Copilot para sugerir configurações](#52-usando-o-copilot-para-sugerir-configurações)  
   - [5.3. Configurações principais da VM](#53-configurações-principais-da-vm)  
   - [5.4. Acessando a VM via SSH](#54-acessando-a-vm-via-ssh)  
6. [Storage Account: armazenando arquivos](#6-storage-account-armazenando-arquivos)  
   - [6.1. Criando um Storage Account](#61-criando-um-storage-account)  
   - [6.2. Criando um container e fazendo upload](#62-criando-um-container-e-fazendo-upload)  
7. [Limpando tudo: deletando o Resource Group](#7-limpando-tudo-deletando-o-resource-group)  
8. [Resumo do que você aprendeu](#8-resumo-do-que-você-aprendeu)  
9. [Próximos passos sugeridos](#9-próximos-passos-sugeridos)  

---

## 1. Conta gratuita no Azure

A Microsoft oferece:

- Uma **conta gratuita** com **US$ 200 em créditos por 30 dias**.  
- Após esse período, **vários serviços populares continuam com camada gratuita**, desde que dentro dos limites de uso definidos.

### Como criar a conta gratuita

1. Acesse o Google e pesquise por:  
   **`Conta gratuita do Azure`**
2. Clique no link oficial da Microsoft (Azure Free Account).  
3. Na página de conta gratuita, você poderá:  
   - Criar sua conta,  
   - Ver os detalhes do benefício,  
   - Ativar seus créditos gratuitos.  
4. Siga o passo a passo do site (será preciso:  
   - Uma conta Microsoft,  
   - Um cartão de crédito para validação,  
   - Dados pessoais básicos).  

Com a conta criada, você poderá seguir todos os labs deste README usando os créditos gratuitos.

---

## 2. Conhecendo o portal do Azure

1. Acesse: **https://portal.azure.com**  
2. Faça login com sua conta Microsoft/Azure.  
3. Você cairá na **Home do portal**.  

Na página inicial você verá:

- **Atividades recentes**: recursos com os quais você mexeu recentemente.  
- A **barra de pesquisa no topo** (recurso mais importante para navegação).  
- Acesso rápido a serviços, notificações e configurações.  

👉 **Dica importante:**  
Assim como na AWS, use SEMPRE a **barra de pesquisa** para localizar recursos, por exemplo:

- `Resource Group`  
- `Virtual Machines`  
- `Storage accounts`  
- `Kubernetes`  
- etc.  

Basta digitar o nome do recurso e clicar no serviço desejado.

---

## 3. Resource Group: a “caixa organizadora”

### 3.1. Conceito

O **Resource Group** (RG) é um dos conceitos mais importantes do Azure.

Pense nele como uma **caixa organizadora** onde você agrupa todos os recursos relacionados a um projeto, aplicação ou sistema, por exemplo:

- Uma aplicação web que usa:
  - Uma VM,
  - Um banco de dados,
  - Um Storage Account,
  - Rede, IPs etc.

Tudo isso pode (e deve) ficar dentro do **mesmo Resource Group**.

**Vantagens:**

- Facilita **organização** dos recursos.  
- Facilita **monitoramento** e **controle de custos**.  
- Facilita **exclusão centralizada**:
  - Você pode apagar **o Resource Group**, e **todos os recursos dentro dele** são removidos juntos.
  - Isso ajuda a evitar deixar “coisas órfãs” que continuam gerando custo.

🔎 Comparando com AWS:

- Na AWS, ao apagar uma instância EC2, você pode deixar para trás discos, Security Groups, IPs etc.  
- No Azure, se tudo estiver dentro de um Resource Group e você apagar o RG, tudo vai embora de uma vez.

---

### 3.2. Criando um Resource Group

1. No portal do Azure, vá até a **barra de pesquisa**.  
2. Digite: **`Resource groups`** e clique no resultado.  
3. Clique em **`Create`**.  

Na tela de criação:

1. **Subscription**  
   - Escolha a assinatura onde serão criados os recursos (por exemplo: *Pay-As-You-Go*).  
2. **Resource group name**  
   - Escolha um nome descritivo, por exemplo:  
     `devops-automation-rg`  
3. **Region**  
   - Escolha uma região (por exemplo, `East US`, `Brazil South` etc.).  

Clique em **`Review + create`** e depois em **`Create`**.

Após alguns instantes:

- Você verá uma notificação no canto superior direito,  
- Pode clicar em **`Go to resource group`** ou voltar na lista de Resource Groups e dar **`Refresh`**.  

Dentro do Resource Group, você tem:

- **Overview**: assinatura, ID, região, deploys.  
- **Access control (IAM)**: controle de acesso.  
- **Tags, Policies, Monitoring, Costs**: outros recursos de gestão.  

Por enquanto, ele está vazio — é apenas a caixa organizadora.

---

## 4. Usando o Cloud Shell do Azure

O **Cloud Shell** é um terminal dentro do próprio portal, que roda em uma máquina gerenciada pela Microsoft.

Você pode usar:

- **Bash**
- **PowerShell**

### Como abrir o Cloud Shell

1. No topo do portal, clique no ícone do **Cloud Shell** (um terminalzinho).  
2. Na primeira vez:  
   - Escolha se quer **Bash** ou **PowerShell** (para DevOps, Bash é muito comum).  
   - Se for solicitado, selecione a Subscription e deixe o Azure criar o armazenamento necessário.  
3. Após provisionar, você terá um terminal Linux/PowerShell disponível.  

Exemplos de comandos:

```bash
ls
ls -la
az --version   # a CLI do Azure já vem instalada
```

Você pode usar o Cloud Shell para:

- Executar comandos da **CLI do Azure** (`az`),  
- Automatizar criação de recursos,  
- Testar scripts rápidos.  

---

## 5. Criando sua primeira Máquina Virtual (VM)

Esta VM será a base de vários labs e automações.  
Aqui vamos criar a VM **pelo portal**, entender as opções, e depois conectar via SSH.

### 5.1. Acessar a tela de criação

1. No portal, use a barra de pesquisa e digite: **`Virtual machines`**.  
2. Clique em **`Virtual machines`**.  
3. Clique em **`Create` → `Azure virtual machine`**.  

---

### 5.2. Usando o Copilot para sugerir configurações

Na tela de criação da VM, você verá:

- As abas de configuração (**Basics, Disks, Networking, Management, etc.**);  
- O **Azure Copilot** (assistente de IA).

Você pode pedir, por exemplo:

- **“Help create a low cost VM”** (me ajude a criar uma VM de baixo custo).  
- **“Help create a highly available VM”** (otimizada para alta disponibilidade).  

O Copilot pode:

- Preencher automaticamente:  
  - Resource Group,  
  - Nome da VM,  
  - Sistema operacional (ex.: Ubuntu),  
  - Tipo de máquina,  
  - Configurações sugeridas de rede.  

Você pode aceitar as sugestões e então apenas ajustar o que for necessário (como usuário/senha, portas etc.).

---

### 5.3. Configurações principais da VM

Na aba **Basics**:

1. **Subscription**  
   - Selecione sua assinatura (ex.: *Pay-As-You-Go*).  

2. **Resource group**  
   - Selecione um existente (ex.: `devops-automation-rg`) ou deixe o Copilot criar um novo.  

3. **Virtual machine name**  
   - Exemplo: `my-lowcost-vm`  

4. **Region**  
   - Escolha uma região próxima ou com melhor custo.  

5. **Image**  
   - Exemplo: `Ubuntu Server` (ex.: 22.04 LTS).  

6. **Size (tamanho da VM)**  
   - Escolha um tipo de VM de baixo custo (o próprio Copilot pode sugerir).  

7. **Authentication type**  
   - Para teste, você pode usar **Password** (usuário/senha).  
   - Em produção, o ideal é **SSH public key**.  

Exemplo de credenciais para laboratório:

- Username: `azuredevops`  
- Password: uma senha forte.  

Marque para permitir tráfego na **porta 22 (SSH)**.

---

#### Disks

Na aba **Disks**, você verá opções como:

- Tipo de disco (Standard HDD, Standard SSD, Premium SSD etc.).  

O próprio portal indica:

- Melhor para produção,  
- Melhor para backup,  
- Melhor para webserver.  

Para laboratório, pode deixar as opções padrão.

---

#### Networking

Na aba **Networking**, o portal geralmente:

- Cria uma **Virtual Network (VNet)** automaticamente.  
- Cria uma **subnet**.  
- Cria um **Public IP**.  
- Cria a **Network Interface (NIC)**.  
- Abre a **porta 22 (SSH)**.  

Há também a opção:

- **Delete public IP and NIC when VM is deleted** → útil para não deixar recursos órfãos.  

---

#### Management, Monitoring, etc.

- Em **Management**, você pode ativar ou não backup e monitoramento (para labs, pode deixar desativado para economizar custos).  
- O painel à direita mostra um **custo estimado mensal** da VM, que se ajusta conforme você muda as configurações.  

Ao final, clique em:

1. **Review + create**  
2. Depois em **Create**  

A VM será provisionada. Ao final, o portal oferece:

- **Go to resource** (ir para a VM criada),  
- **Create another VM**.  

Clique em **Go to resource**.

---

### 5.4. Acessando a VM via SSH

Dentro da página da VM:

1. Clique em **`Connect` → `SSH`**.  
2. O portal mostrará:  
   - O IP público,  
   - O usuário,  
   - O comando SSH sugerido.  

No seu terminal local:

```bash
ssh azuredevops@SEU_IP_PUBLICO
```

- Digite a senha que você configurou na criação da VM.  
- Ao conectar, você estará dentro da VM no Azure.  

Exemplo de comandos:

```bash
uname -a
ls
```

Se quiser sair da VM:

```bash
exit
```

---

## 6. Storage Account: armazenando arquivos

O **Storage Account** é muito usado em automações para:

- Guardar **logs**,  
- Armazenar **arquivos de state** (por exemplo, Terraform state),  
- Guardar arquivos estáticos em geral.  

Aqui o objetivo é entender a **estrutura básica** pelo portal.

---

### 6.1. Criando um Storage Account

1. No portal, use a barra de pesquisa e digite: **`Storage accounts`**.  
2. Clique em **`Storage accounts`**.  
3. Clique em **`Create`**.  

Na aba **Basics**:

1. **Subscription**  
   - Sua assinatura.  

2. **Resource group**  
   - Use o mesmo RG que sua VM (ex.: `devops-automation-rg`), assim você consegue deletar tudo junto depois.  

3. **Storage account name**  
   - Deve ser **único globalmente** e em minúsculas, sem caracteres especiais.  
   - Exemplo: `devopsautomationsa123`  
   - Se o nome já estiver em uso, o portal avisará e você terá que escolher outro.  

4. **Region**  
   - Mesma região da VM ou próxima.  

5. **Performance**  
   - Geralmente `Standard` é suficiente para labs.  

6. **Redundancy**  
   - Ex.: `GRS`, `LRS` etc. (para laboratório, pode deixar o padrão ou uma opção mais simples).  

Você pode passar rapidamente pelas abas:

- **Advanced**  
- **Networking**  
- **Data protection**  

Se o objetivo é só laboratório, pode usar o padrão e clicar direto em:

- **Review + create**  
- **Create**  

Ao final, clique em **Go to resource**.

---

### 6.2. Criando um container e fazendo upload

Dentro do seu **Storage Account**:

1. No menu lateral, clique em **Containers**.  
2. Clique em **`+ Container`**.  
3. Dê um nome, por exemplo: `tfstate` (simulando um container para state do Terraform).  
4. Defina o nível de acesso (para labs, `Private` é suficiente).  
5. Clique em **Create**.  

Agora, dentro do container `tfstate`:

1. Clique em **`Upload`**.  
2. Selecione um arquivo qualquer do seu computador (ex.: `file1.txt`).  
3. Clique em **Upload**.  

Você verá o arquivo listado no container.  
Ao clicar no arquivo, é possível:

- Ver detalhes,  
- Baixar,  
- E em alguns casos até **editar** o conteúdo diretamente pelo portal (arquivos de texto).  

---

## 7. Limpando tudo: deletando o Resource Group

Para não gerar custos desnecessários, o ideal é **sempre deletar tudo que não estiver usando**.

A forma mais prática é apagar o **Resource Group** que contém:

- A VM,  
- O IP público,  
- A Network Interface,  
- A Virtual Network,  
- O Storage Account,  
- E demais recursos associados.  

### Como deletar o Resource Group

1. No portal, vá em **Resource groups**.  
2. Clique no grupo que você usou para o lab (ex.: `devops-automation-rg`).  
3. Clique em **`Delete resource group`**.  
4. O portal vai pedir para você:  
   - Digitar o **nome exato** do Resource Group para confirmar,  
   - (Opcional) Marcar uma caixa de confirmação adicional.  
5. Clique em **Delete**.  

O Azure:

- Vai iniciar o processo de deleção,  
- Mostrará o status nas notificações,  
- Levará alguns instantes para remover todos os recursos.  

👉 **Boa prática:**  
Depois de deletar:

1. Volte na **Home**.  
2. Verifique de novo em **Resource groups**, **Virtual machines**, **Storage accounts** etc., para garantir que não ficou nada para trás.  

---

## 8. Resumo do que você aprendeu

Com este lab inicial de Azure, você já sabe:

- Como **criar e usar uma conta gratuita** com créditos.  
- Como navegar no **portal do Azure** usando a barra de pesquisa.  
- O que é um **Resource Group** e como ele organiza recursos de um projeto.  
- Como acessar e usar o **Cloud Shell** para comandos rápidos.  
- Como criar uma **máquina virtual**:  
  - Usando o assistente e o **Copilot** para sugerir configurações,  
  - Escolhendo sistema operacional, tamanho, rede, autenticação,  
  - Visualizando o **custo estimado** da VM.  
- Como **acessar a VM via SSH**.  
- Como criar um **Storage Account** e um **container**, e fazer upload de arquivos.  
- Como **deletar o Resource Group** para remover tudo de forma centralizada e evitar custos.  

---

## 9. Próximos passos sugeridos

Para aprofundar seu conhecimento em Azure e DevOps:

- Criar uma VM em **rede privada** e acessá-la via **bastion** ou **jump host**.  
- Explorar:  
  - **Azure Kubernetes Service (AKS)**,  
  - **Azure SQL / Cosmos DB**,  
  - **Azure DevOps** ou **GitHub Actions** para CI/CD,  
  - **Azure Monitor** e **Application Insights** para logs e métricas.  
- Integrar o ambiente com:  
  - **Terraform** (Infraestrutura como Código),  
  - **Ansible** (configuração e provisionamento),  
  - Containers com **Docker** e **Azure Container Registry**.  
