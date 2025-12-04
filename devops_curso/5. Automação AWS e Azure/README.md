# Guia de Labs com AWS CLI e Azure CLI

Este documento integra, em um único material, labs práticos utilizando **AWS CLI** e **Azure CLI** para criação, manipulação e automação de recursos em nuvem. O conteúdo está organizado de forma impessoal e progressiva, facilitando o uso em estudos, aulas e práticas de DevOps.

---

## Parte I – Labs com AWS CLI

### Lab 1 – Criar e Manipular Buckets S3 com AWS CLI

#### 1. Objetivo

Demonstrar a criação e a manipulação de buckets e objetos no **Amazon S3** utilizando apenas a **AWS CLI**, sem interface gráfica.

#### 2. Pré-requisitos

- AWS CLI instalada e configurada (`aws configure`);
- Credenciais com permissões para S3.

#### 3. Criar um bucket S3

```bash
aws s3api create-bucket --bucket meu-lab-s3 --region us-east-1
```

- Cria um bucket chamado `meu-lab-s3` na região `us-east-1`.
- O nome do bucket deve ser **globalmente único**.

#### 4. Listar todos os buckets S3 da conta

```bash
aws s3api list-buckets --query "Buckets[].Name"
```

- Lista os nomes de todos os buckets S3 existentes na conta.

#### 5. Enviar um arquivo para o bucket

```bash
echo "teste" > arquivo.txt
aws s3 cp arquivo.txt s3://meu-lab-s3/
```

- Cria um arquivo local `arquivo.txt` e envia para o bucket `meu-lab-s3`.

#### 6. Listar arquivos dentro do bucket

```bash
aws s3 ls s3://meu-lab-s3/
```

- Lista todos os objetos armazenados no bucket.

#### 7. Baixar um arquivo do bucket

```bash
aws s3 cp s3://meu-lab-s3/arquivo.txt arquivo-download.txt
```

- Baixa o objeto `arquivo.txt` do bucket e salva como `arquivo-download.txt` localmente.

#### 8. Criar uma pasta (prefixo) no bucket

```bash
aws s3api put-object --bucket meu-lab-s3 --key pasta1/
```

- Cria um prefixo lógico `pasta1/` dentro do bucket (equivalente a uma “pasta”).

---

### Lab 2 – Criar e Manipular VMs na AWS via CLI

#### 1. Objetivo

Criar e gerenciar instâncias **EC2** na AWS utilizando a linha de comando, explorando VPC e subnets padrão e uso de variáveis para reaproveitamento de configuração.

#### 2. Pré-requisitos

- AWS CLI instalada e configurada (`aws configure`);
- Permissões para EC2, VPC, rede e chaves (IAM).

#### 3. Variáveis iniciais do ambiente

```bash
VPC_ID=$(aws ec2 describe-vpcs   --filters Name=isDefault,Values=true   --query "Vpcs[0].VpcId"   --output text)

SUBNET_ID=$(aws ec2 describe-subnets   --filters Name=default-for-az,Values=true   --query "Subnets[0].SubnetId"   --output text)

KEY_NAME="devops-keypair"
SG_NAME="devops-sg-ie"
```

- `VPC_ID`: ID da VPC padrão.
- `SUBNET_ID`: ID de uma subnet padrão.
- `KEY_NAME`: nome do par de chaves SSH.
- `SG_NAME`: nome do Security Group a ser criado.

#### 4. Criar par de chaves para acesso via SSH

```bash
aws ec2 create-key-pair   --key-name "$KEY_NAME"   --query 'KeyMaterial'   --output text > "$KEY_NAME.pem"

chmod 400 "$KEY_NAME.pem"
```

- Gera a chave privada e salva no arquivo `devops-keypair.pem`.
- As permissões são ajustadas para uso seguro com SSH.

#### 5. Criar Security Group

```bash
SG_ID=$(aws ec2 create-security-group   --group-name "$SG_NAME"   --description "Acesso SSH"   --vpc-id "$VPC_ID"   --query 'GroupId'   --output text)
```

- Cria um Security Group vinculado à VPC padrão e captura o ID em `SG_ID`.

#### 6. Liberar acesso SSH (porta 22)

```bash
aws ec2 authorize-security-group-ingress   --group-id "$SG_ID"   --protocol tcp   --port 22   --cidr 0.0.0.0/0
```

- Libera acesso SSH (porta 22) a partir de qualquer IP (uso didático; não recomendado em produção).

#### 7. Obter ID de uma AMI Amazon Linux 2

```bash
AMI_ID=$(aws ec2 describe-images   --owners amazon   --filters "Name=name,Values=amzn2-ami-hvm-*-x86_64-gp2" "Name=state,Values=available"   --query 'Images | sort_by(@, &CreationDate) | [-1].ImageId'   --output text)
```

- Seleciona a AMI mais recente do tipo Amazon Linux 2.

#### 8. Criar instância EC2

```bash
INSTANCE_INFO=$(aws ec2 run-instances   --image-id "$AMI_ID"   --count 1   --instance-type t2.micro   --key-name "$KEY_NAME"   --security-group-ids "$SG_ID"   --subnet-id "$SUBNET_ID"   --associate-public-ip-address   --query 'Instances[0].[InstanceId, PublicIpAddress]'   --output text)

INSTANCE_ID=$(echo "$INSTANCE_INFO" | awk '{print $1}')
PUBLIC_IP=$(echo "$INSTANCE_INFO" | awk '{print $2}')

echo "Instância criada: $INSTANCE_ID"
echo "IP Público: $PUBLIC_IP"
```

- Cria uma instância do tipo `t2.micro`, associa IP público e captura ID e IP.

#### 9. Conectar via SSH

```bash
ssh -i "$KEY_NAME.pem" ec2-user@"$PUBLIC_IP"
```

- Estabelece conexão SSH com a instância criada.

#### 10. Parar, iniciar e terminar a instância

```bash
aws ec2 stop-instances --instance-ids "$INSTANCE_ID"
aws ec2 start-instances --instance-ids "$INSTANCE_ID"
aws ec2 terminate-instances --instance-ids "$INSTANCE_ID"
```

#### 11. Limpeza de recursos

```bash
aws ec2 delete-security-group --group-id "$SG_ID"
rm "$KEY_NAME.pem"
```

- Remove o Security Group criado e o arquivo local da chave.

---

### Lab 3 – Criar VMs em Lote com Script Bash na AWS CLI

#### 1. Objetivo

Automatizar a criação de múltiplas instâncias EC2 utilizando um script em Bash com loops e variáveis.

#### 2. Estrutura de diretório

```bash
mkdir -p ~/labs/aws/vm-lote
cd ~/labs/aws/vm-lote
touch criar-vms.sh
chmod +x criar-vms.sh
```

#### 3. Script `criar-vms.sh`

```bash
#!/bin/bash

KEY_NAME="devops-keypair"
SG_NAME="devops-sg-ie"

VPC_ID=$(aws ec2 describe-vpcs   --filters Name=isDefault,Values=true   --query "Vpcs[0].VpcId" --output text)

SUBNET_ID=$(aws ec2 describe-subnets   --filters Name=default-for-az,Values=true   --query "Subnets[0].SubnetId" --output text)

AMI_ID=$(aws ec2 describe-images   --owners amazon   --filters "Name=name,Values=amzn2-ami-hvm-*-x86_64-gp2"   --query 'Images | sort_by(@, &CreationDate) | [-1].ImageId'   --output text)

# Verifica se a key pair já existe
aws ec2 describe-key-pairs --key-names "$KEY_NAME" >/dev/null 2>&1
if [ $? -ne 0 ]; then
  echo "Criando key pair $KEY_NAME"
  aws ec2 create-key-pair --key-name "$KEY_NAME"     --query 'KeyMaterial' --output text > "$KEY_NAME.pem"
  chmod 400 "$KEY_NAME.pem"
else
  echo "Key pair $KEY_NAME já existe na AWS."
  if [ ! -f "$KEY_NAME.pem" ]; then
    echo "Arquivo local $KEY_NAME.pem não encontrado. Ajuste antes de continuar."
    exit 1
  fi
fi

# Criar Security Group
SG_ID=$(aws ec2 create-security-group   --group-name "$SG_NAME"   --description "Acesso via script em lote"   --vpc-id "$VPC_ID"   --query 'GroupId' --output text)

# Liberar porta 22
aws ec2 authorize-security-group-ingress   --group-id "$SG_ID" --protocol tcp --port 22 --cidr 0.0.0.0/0

# Lista de VMs a criar
VMS=(vm01 vm02 vm03)

for NAME in "${VMS[@]}"; do
  echo "Criando instância: $NAME"

  INSTANCE_ID=$(aws ec2 run-instances     --image-id "$AMI_ID"     --count 1     --instance-type t2.micro     --key-name "$KEY_NAME"     --security-group-ids "$SG_ID"     --subnet-id "$SUBNET_ID"     --associate-public-ip-address     --tag-specifications "ResourceType=instance,Tags=[{Key=Name,Value=$NAME}]"     --query 'Instances[0].InstanceId' --output text)

  echo "$NAME criada com ID: $INSTANCE_ID"

  aws ec2 wait instance-running --instance-ids "$INSTANCE_ID"
  echo "$NAME está em execução"
done

echo "Criação em lote concluída."
```

#### 4. Executar e validar

```bash
./criar-vms.sh

aws ec2 describe-instances   --filters "Name=tag:Name,Values=vm01,vm02,vm03"   --query "Reservations[].Instances[].PublicIpAddress" --output text
```

---

### Lab 4 – Script para Destruir VMs e Recursos na AWS via CLI

#### 1. Objetivo

Remover instâncias EC2 criadas em lote e limpar recursos associados, como Security Group e key pair, evitando custos desnecessários.

#### 2. Estrutura do script

```bash
cd ~/labs/aws/vm-lote
touch destruir-vms.sh
chmod +x destruir-vms.sh
```

#### 3. Conteúdo de `destruir-vms.sh`

```bash
#!/bin/bash

export AWS_PAGER=""

KEY_NAME="devops-keypair"
SG_NAME="devops-sg-ie"

# Lista de nomes criados
VMS=(vm01 vm02 vm03)

# Coletar Instance IDs
INSTANCE_IDS=()

for NAME in "${VMS[@]}"; do
  INSTANCE_ID=$(aws ec2 describe-instances     --filters "Name=tag:Name,Values=$NAME" "Name=instance-state-name,Values=running,stopped"     --query "Reservations[*].Instances[*].InstanceId" --output text)

  if [ -n "$INSTANCE_ID" ]; then
    echo "Finalizando $NAME com ID $INSTANCE_ID"
    aws ec2 terminate-instances --instance-ids "$INSTANCE_ID"
    INSTANCE_IDS+=($INSTANCE_ID)
  else
    echo "Instância $NAME não encontrada ou já terminada"
  fi
done

# Aguardar finalização de todas as instâncias
if [ ${#INSTANCE_IDS[@]} -gt 0 ]; then
  echo "Aguardando término das instâncias..."
  aws ec2 wait instance-terminated --instance-ids "${INSTANCE_IDS[@]}"
  echo "Instâncias finalizadas com sucesso"
else
  echo "Nenhuma instância para aguardar término"
fi

# Deletar Security Group
SG_ID=$(aws ec2 describe-security-groups   --group-names "$SG_NAME"   --query 'SecurityGroups[0].GroupId' --output text 2>/dev/null)

if [ -n "$SG_ID" ]; then
  echo "Removendo Security Group..."
  aws ec2 delete-security-group --group-id "$SG_ID"
  echo "Security Group removido com sucesso"
else
  echo "Security Group $SG_NAME não encontrado ou já removido"
fi

# Deletar key pair remota e arquivo local
aws ec2 delete-key-pair --key-name "$KEY_NAME"
rm -f "$KEY_NAME.pem"
echo "Key pair e arquivo local removidos."
```

#### 4. Execução

```bash
./destruir-vms.sh
```

---

## Parte II – Labs com Azure CLI

### Lab 5 – Introdução à Azure CLI

#### 1. Objetivo

Apresentar os primeiros comandos da **Azure CLI** para autenticação e consulta básica de subscriptions, Resource Groups e recursos, mesmo sem infraestrutura provisionada.

#### 2. Pré-requisitos

- Conta ativa na Azure;
- Azure CLI instalada.

#### 3. Login na Azure

```bash
az login
```

- Inicia o fluxo de autenticação e vincula a sessão local à conta Azure.

#### 4. Listar subscriptions

```bash
az account list --output table
```

- Lista as subscriptions às quais a conta autenticada possui acesso.

#### 5. Listar Resource Groups existentes

```bash
az group list --output table
```

- Lista todos os Resource Groups da subscription atual.

Para consultar um grupo específico:

```bash
az group show --name terraform-demo-rg --output table
```

#### 6. Listar recursos de um Resource Group

```bash
az resource list --resource-group terraform-demo-rg --output table
```

- Lista os recursos associados ao Resource Group especificado.
- Em caso de grupo vazio, o retorno será uma lista vazia.

#### 7. Testar listagem de VMs

```bash
az vm list --output table
```

- Verifica o funcionamento da CLI, mesmo sem VMs criadas.

Exemplo com filtragem:

```bash
az vm list --query "[].{name:name, location:location}" --output table
```

---

### Lab 6 – Criar VMs em Lote via Bash + Azure CLI

#### 1. Objetivo

Criar múltiplas máquinas virtuais na Azure, primeiro por comandos manuais e depois com automação simples via script Bash e Azure CLI.

#### 2. Pré-requisitos

- Azure CLI instalada e autenticada (`az login`);
- Permissões para criação de Resource Groups e VMs.

#### 3. Criação de VMs manualmente

##### 3.1 Criar Resource Group

```bash
az group create --name devops-automation --location eastus
```

##### 3.2 Definir variáveis

```bash
RG="devops-automation"
LOCATION="eastus"
PASSWORD="SenhaForte123"
```

##### 3.3 Criar VMs

```bash
az vm create   --resource-group $RG   --name vm01   --image Ubuntu2204   --admin-username azureuser   --admin-password $PASSWORD   --authentication-type password   --location $LOCATION

az vm create   --resource-group $RG   --name vm02   --image Ubuntu2204   --admin-username azureuser   --admin-password $PASSWORD   --authentication-type password   --location $LOCATION
```

##### 3.4 Verificar VMs criadas

```bash
az vm list --resource-group $RG --output table
```

---

#### 4. Explorar propriedades das VMs

##### 4.1 Listar IPs públicos

```bash
az vm list-ip-addresses --resource-group $RG --output table
```

##### 4.2 Exibir detalhes de uma VM

```bash
az vm show --resource-group $RG --name vm01 --output json
```

##### 4.3 Obter status da instância

```bash
az vm get-instance-view   --resource-group $RG   --name vm01   --query "instanceView.statuses[*].displayStatus"   --output table
```

##### 4.4 Listar discos, NICs e NSGs

```bash
az disk list --resource-group $RG --output table
az network nic list --resource-group $RG --output table
az network nsg list --resource-group $RG --output table
```

##### 4.5 Obter IP público diretamente

```bash
az vm list-ip-addresses --resource-group $RG --name vm01   --query "[].virtualMachine.network.publicIpAddresses[].ipAddress"   --output tsv
```

---

#### 5. Remover VMs criadas manualmente

```bash
az vm delete --resource-group $RG --name vm01 --yes
az vm delete --resource-group $RG --name vm02 --yes

az vm list --resource-group $RG --output table
```

---

#### 6. Transformar em script automatizado

##### 6.1 Estrutura e criação do script

```bash
mkdir -p ~/labs/azure/vm-lote
cd ~/labs/azure/vm-lote
touch criar-vms.sh
chmod +x criar-vms.sh
```

##### 6.2 Conteúdo de `criar-vms.sh`

```bash
#!/bin/bash

RESOURCE_GROUP="devops-automation"
LOCATION="brazilsouth"
PASSWORD="SenhaForte123!"

criar_vm() {
  local NOME_VM=$1
  echo "Criando VM: $NOME_VM"

  az vm create     --resource-group $RESOURCE_GROUP     --name $NOME_VM     --image Ubuntu2204     --admin-username azureuser     --admin-password $PASSWORD     --authentication-type password     --location $LOCATION     --no-wait
}

# Lista de VMs para criar
VMS=(vm01 vm02)

for nome in "${VMS[@]}"; do
  criar_vm "$nome"
done

echo "Criação em lote iniciada. Aguarde o provisionamento das VMs."
```

##### 6.3 Execução

```bash
./criar-vms.sh
```

---

### Lab 7 – Filtrar e Salvar Informações com Azure CLI + jq/awk

#### 1. Objetivo

Utilizar Azure CLI em conjunto com ferramentas de linha de comando (`jq`, `awk`) para filtrar, formatar e armazenar informações de VMs (nome, IP e status) em arquivos de texto reutilizáveis.

#### 2. Pré-requisitos

- VMs criadas (por exemplo, `vm01` e `vm02`);
- Azure CLI instalada e autenticada;
- `jq` e `awk` instalados no ambiente.

---

#### 3. Listar e salvar IPs públicos

##### 3.1 Ver saída bruta da Azure CLI

```bash
az vm list-ip-addresses --resource-group devops-automation --output json
```

##### 3.2 Filtrar nome e IP com Azure CLI + jq

```bash
az vm list-ip-addresses --resource-group devops-automation   --query "[].virtualMachine.{name:name, ip:network.publicIpAddresses[0].ipAddress}"   --output json | jq -r '.[] | "\(.name) \(.ip)"'
```

##### 3.3 Salvar IPs em arquivo texto

```bash
az vm list-ip-addresses --resource-group devops-automation   --query "[].virtualMachine.{name:name, ip:network.publicIpAddresses[0].ipAddress}"   --output json | jq -r '.[] | "\(.name) \(.ip)"' > vms-ips.txt
```

##### 3.4 Verificar o conteúdo

```bash
cat vms-ips.txt
```

Exemplo de conteúdo:

```text
vm01 20.120.45.101
vm02 20.120.45.102
```

##### 3.5 Extrair IPs específicos com awk

```bash
IP_VM1=$(awk '$1 == "vm01" { print $2 }' vms-ips.txt)
IP_VM2=$(awk '$1 == "vm02" { print $2 }' vms-ips.txt)

echo "$IP_VM1"
echo "$IP_VM2"
```

---

#### 4. Extrair status das VMs

##### 4.1 Ver saída bruta do status

```bash
az vm get-instance-view --resource-group devops-automation --name vm01 --output json
```

##### 4.2 Coletar status de múltiplas VMs

```bash
for vm in vm01 vm02; do
  az vm get-instance-view     --resource-group devops-automation     --name "$vm"     --query "instanceView.statuses[?starts_with(code,'PowerState/')].displayStatus"     --output tsv >> status.txt
done
```

##### 4.3 Verificar status coletados

```bash
cat status.txt
```

---

#### 5. Reformatar saída com awk

```bash
awk '{ print "VM:" $1 " | IP:" $2 }' vms-ips.txt
```

- Formata as informações de forma mais legível, útil para logs e relatórios.

---

## Considerações Finais

Este guia reúne, em um único documento, labs práticos de **AWS CLI** e **Azure CLI** cobrindo:

- Criação e manipulação de buckets S3;
- Criação, automação e destruição de instâncias EC2;
- Autenticação e inspeção de recursos na Azure;
- Criação de VMs em lote com scripts Bash;
- Filtragem de informações de VMs com `jq` e `awk`.

O material pode ser utilizado tanto como roteiro de laboratório quanto como referência rápida para automação de infraestrutura em nuvem em contexto de DevOps.