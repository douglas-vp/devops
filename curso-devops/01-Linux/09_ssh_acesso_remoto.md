# Uso de SSH para acesso remoto

O **SSH** significa **Secure Shell**. Ele permite acessar remotamente outro computador ou servidor Linux de forma segura pelo terminal.

A estrutura básica é:

```bash
ssh usuario@ip_ou_dominio
```

Exemplo:

```bash
ssh ubuntu@192.168.0.10
```

ou:

```bash
ssh ubuntu@meuservidor.com.br
```

---

## 1. Verificar se o SSH está instalado

### No computador cliente

O cliente é a máquina de onde será feito o acesso ao servidor.

```bash
ssh -V
```

Se aparecer a versão do OpenSSH, o cliente SSH está instalado.

### No servidor

O servidor precisa ter o serviço SSH instalado e ativo.

No Ubuntu/Debian:

```bash
sudo apt update
sudo apt install openssh-server -y
```

Verificar status:

```bash
sudo systemctl status ssh
```

Iniciar o serviço:

```bash
sudo systemctl start ssh
```

Habilitar no boot:

```bash
sudo systemctl enable ssh
```

---

## 2. Descobrir o IP do servidor

No servidor, execute:

```bash
hostname -I
```

ou:

```bash
ip addr
```

Exemplo de IP local:

```bash
192.168.0.10
```

---

## 3. Acessar servidor com usuário e senha

No computador cliente:

```bash
ssh usuario@ip_do_servidor
```

Exemplo:

```bash
ssh douglas@192.168.0.10
```

Na primeira conexão, pode aparecer uma mensagem parecida com:

```text
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

Digite:

```bash
yes
```

Depois informe a senha do usuário remoto.

---

## 4. Acessar servidor usando domínio

Se o servidor tiver domínio configurado, use:

```bash
ssh usuario@dominio.com.br
```

Exemplo:

```bash
ssh ubuntu@servidor.technium.me
```

---

## 5. Acessar servidor em porta diferente

Por padrão, o SSH usa a porta `22`.

Se o servidor usa outra porta, informe com `-p`:

```bash
ssh usuario@ip_do_servidor -p 2222
```

Exemplo:

```bash
ssh ubuntu@192.168.0.10 -p 2222
```

---

## 6. Gerar chave SSH

A forma mais segura e prática de acessar servidores é usando chave SSH.

No computador cliente, gere uma chave:

```bash
ssh-keygen -t ed25519 -C "seu_email@example.com"
```

Pressione `Enter` para aceitar o local padrão:

```bash
~/.ssh/id_ed25519
```

Arquivos criados:

| Arquivo | Função |
|---|---|
| `~/.ssh/id_ed25519` | Chave privada |
| `~/.ssh/id_ed25519.pub` | Chave pública |

A chave privada nunca deve ser compartilhada.

---

## 7. Copiar chave pública para o servidor

Use:

```bash
ssh-copy-id usuario@ip_do_servidor
```

Exemplo:

```bash
ssh-copy-id douglas@192.168.0.10
```

Se o SSH usa porta diferente:

```bash
ssh-copy-id -p 2222 usuario@ip_do_servidor
```

Depois, acesse sem senha:

```bash
ssh douglas@192.168.0.10
```

---

## 8. Copiar chave manualmente

Se `ssh-copy-id` não estiver disponível, copie o conteúdo da chave pública:

```bash
cat ~/.ssh/id_ed25519.pub
```

No servidor, adicione esse conteúdo ao arquivo:

```bash
~/.ssh/authorized_keys
```

Passos no servidor:

```bash
mkdir -p ~/.ssh
nano ~/.ssh/authorized_keys
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

---

## 9. Acessar usando chave específica

Se a chave tiver outro nome ou caminho:

```bash
ssh -i caminho_da_chave usuario@ip_do_servidor
```

Exemplo:

```bash
ssh -i ~/.ssh/minha_chave ubuntu@192.168.0.10
```

Para arquivos `.pem`, comum em ambientes de nuvem:

```bash
ssh -i chave.pem ubuntu@ip_do_servidor
```

Se houver erro de permissão:

```bash
chmod 600 chave.pem
```

Depois tente novamente:

```bash
ssh -i chave.pem ubuntu@ip_do_servidor
```

---

## 10. Arquivo de configuração SSH

Para simplificar acessos frequentes, use o arquivo:

```bash
~/.ssh/config
```

Criar ou editar:

```bash
nano ~/.ssh/config
```

Exemplo:

```sshconfig
Host minha-vm
    HostName 192.168.0.10
    User ubuntu
    Port 22
    IdentityFile ~/.ssh/id_ed25519
```

Depois acesse com:

```bash
ssh minha-vm
```

Permissão recomendada:

```bash
chmod 600 ~/.ssh/config
```

---

## 11. Copiar arquivos com SCP

O `scp` copia arquivos usando SSH.

### Copiar arquivo local para servidor

```bash
scp arquivo.txt usuario@ip_do_servidor:/caminho/destino
```

Exemplo:

```bash
scp arquivo.txt ubuntu@192.168.0.10:/home/ubuntu/
```

### Copiar arquivo do servidor para sua máquina

```bash
scp usuario@ip_do_servidor:/caminho/arquivo.txt .
```

Exemplo:

```bash
scp ubuntu@192.168.0.10:/home/ubuntu/log.txt .
```

### Copiar pasta inteira

```bash
scp -r pasta usuario@ip_do_servidor:/caminho/destino
```

Exemplo:

```bash
scp -r projeto ubuntu@192.168.0.10:/home/ubuntu/
```

### Usar porta diferente com SCP

No `scp`, a porta é informada com `-P` maiúsculo:

```bash
scp -P 2222 arquivo.txt usuario@ip:/destino
```

---

## 12. Copiar arquivos com RSYNC

O `rsync` é melhor para sincronizar pastas, pois copia apenas diferenças.

```bash
rsync -av pasta/ usuario@ip_do_servidor:/caminho/destino/
```

Exemplo:

```bash
rsync -av projeto/ ubuntu@192.168.0.10:/home/ubuntu/projeto/
```

Com porta diferente:

```bash
rsync -av -e "ssh -p 2222" projeto/ usuario@ip:/destino/
```

---

## 13. Executar comando remoto via SSH

É possível executar um comando no servidor sem abrir uma sessão interativa:

```bash
ssh usuario@ip_do_servidor "comando"
```

Exemplo:

```bash
ssh ubuntu@192.168.0.10 "df -h"
```

Outro exemplo:

```bash
ssh ubuntu@192.168.0.10 "sudo systemctl status nginx"
```

---

## 14. Túnel SSH local

Um túnel local permite acessar uma porta remota como se estivesse na sua máquina.

Estrutura:

```bash
ssh -L porta_local:localhost:porta_remota usuario@servidor
```

Exemplo para acessar um serviço remoto na porta `3000`:

```bash
ssh -L 3000:localhost:3000 ubuntu@192.168.0.10
```

Depois acesse no navegador local:

```text
http://localhost:3000
```

---

## 15. Ver logs do SSH no servidor

No Ubuntu/Debian:

```bash
sudo journalctl -u ssh
```

Em tempo real:

```bash
sudo journalctl -u ssh -f
```

Também pode verificar:

```bash
sudo tail -f /var/log/auth.log
```

---

## 16. Arquivos importantes do SSH

| Caminho | Função |
|---|---|
| `~/.ssh/id_ed25519` | Chave privada do usuário |
| `~/.ssh/id_ed25519.pub` | Chave pública do usuário |
| `~/.ssh/authorized_keys` | Chaves públicas autorizadas no servidor |
| `~/.ssh/config` | Configurações de conexão do cliente SSH |
| `/etc/ssh/sshd_config` | Configuração do servidor SSH |
| `/var/log/auth.log` | Logs de autenticação no Ubuntu/Debian |

---

## 17. Permissões recomendadas

| Caminho | Permissão |
|---|---|
| `~/.ssh` | `700` |
| `~/.ssh/id_ed25519` | `600` |
| `~/.ssh/id_ed25519.pub` | `644` |
| `~/.ssh/authorized_keys` | `600` |
| `~/.ssh/config` | `600` |
| `chave.pem` | `600` |

Aplicar permissões:

```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_ed25519
chmod 644 ~/.ssh/id_ed25519.pub
chmod 600 ~/.ssh/authorized_keys
chmod 600 ~/.ssh/config
```

---

## 18. Boas práticas de segurança

- Use chave SSH em vez de senha sempre que possível.
- Não compartilhe a chave privada.
- Use usuários comuns com `sudo`, evitando login direto como `root`.
- Mantenha o SSH atualizado.
- Desative login por senha apenas depois de testar o acesso por chave.
- Antes de fechar a sessão atual, abra outro terminal e teste o acesso por chave para evitar perder acesso ao servidor.

Atualizar sistema no Ubuntu/Debian:

```bash
sudo apt update
sudo apt upgrade -y
```

Editar configuração do servidor SSH:

```bash
sudo nano /etc/ssh/sshd_config
```

Configurações recomendadas:

```text
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
```

Reiniciar SSH:

```bash
sudo systemctl restart ssh
```

---

## 19. Problemas comuns

### Permission denied publickey

| Possível causa | Solução |
|---|---|
| Chave errada | Usar `ssh -i caminho_da_chave usuario@ip` |
| Usuário errado | Conferir usuário remoto |
| Chave pública ausente no servidor | Adicionar chave em `~/.ssh/authorized_keys` |
| Permissões incorretas | Ajustar permissões com `chmod` |
| Servidor ou serviço não aceita a chave | Cadastrar a chave pública no serviço correto |

---

### Host key verification failed

Pode ocorrer quando o IP ou servidor mudou.

Remover entrada antiga:

```bash
ssh-keygen -R ip_ou_dominio
```

Depois conectar novamente:

```bash
ssh usuario@ip_ou_dominio
```

---

### Connection refused

| Possível causa | Verificação |
|---|---|
| SSH não instalado | `sudo apt install openssh-server -y` |
| Serviço parado | `sudo systemctl status ssh` |
| Porta incorreta | `ssh usuario@ip -p porta` |
| Firewall bloqueando | Verificar regras de firewall |
| IP incorreto | Conferir com `hostname -I` |

---

## 20. Resumo dos comandos principais

| Ação | Comando |
|---|---|
| Acessar servidor | `ssh usuario@ip` |
| Acessar com porta específica | `ssh usuario@ip -p 2222` |
| Acessar com chave | `ssh -i chave.pem usuario@ip` |
| Gerar chave SSH | `ssh-keygen -t ed25519 -C "email"` |
| Copiar chave para servidor | `ssh-copy-id usuario@ip` |
| Copiar arquivo para servidor | `scp arquivo.txt usuario@ip:/destino` |
| Copiar arquivo do servidor | `scp usuario@ip:/arquivo.txt .` |
| Copiar pasta | `scp -r pasta usuario@ip:/destino` |
| Sincronizar pasta | `rsync -av pasta/ usuario@ip:/destino/` |
| Executar comando remoto | `ssh usuario@ip "comando"` |
| Criar túnel local | `ssh -L 3000:localhost:3000 usuario@ip` |
| Ver logs SSH | `sudo journalctl -u ssh -f` |
| Corrigir permissão de chave `.pem` | `chmod 600 chave.pem` |
| Remover host antigo | `ssh-keygen -R ip_ou_dominio` |

---

## 21. Fluxo recomendado de uso

```bash
ssh-keygen -t ed25519 -C "seu_email@example.com"
ssh-copy-id usuario@ip_do_servidor
ssh usuario@ip_do_servidor
```

Para servidor com chave específica:

```bash
chmod 600 chave.pem
ssh -i chave.pem usuario@ip_do_servidor
```
