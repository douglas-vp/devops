# Comandos Essenciais do Linux

Este documento reúne os principais comandos Linux em formato de tabela, organizados por categoria, com descrição e exemplo de uso.

---

## 1. Navegação entre diretórios

| Comando | Descrição | Exemplo |
|---|---|---|
| `pwd` | Mostra o diretório atual. | `pwd` |
| `ls` | Lista arquivos e pastas do diretório atual. | `ls` |
| `ls -la` | Lista arquivos e pastas com detalhes, incluindo arquivos ocultos. | `ls -la` |
| `cd nome_da_pasta` | Entra em uma pasta. | `cd Documentos` |
| `cd ..` | Volta um nível na estrutura de diretórios. | `cd ..` |
| `cd ~` | Vai para a pasta pessoal do usuário. | `cd ~` |
| `cd` | Vai para a pasta pessoal do usuário. | `cd` |
| `cd /` | Vai para o diretório raiz do sistema. | `cd /` |

---

## 2. Manipulação de arquivos e pastas

| Comando | Descrição | Exemplo |
|---|---|---|
| `mkdir nome_da_pasta` | Cria uma nova pasta. | `mkdir projetos` |
| `touch arquivo.txt` | Cria um arquivo vazio. | `touch notas.txt` |
| `cp origem destino` | Copia um arquivo para outro local. | `cp arquivo.txt /home/usuario/Documentos/` |
| `cp -r pasta_origem pasta_destino` | Copia uma pasta com todo o seu conteúdo. | `cp -r projeto backup_projeto` |
| `mv origem destino` | Move um arquivo ou pasta para outro local. | `mv arquivo.txt /home/usuario/Downloads/` |
| `mv nome_antigo nome_novo` | Renomeia um arquivo ou pasta. | `mv relatorio.txt relatorio_final.txt` |
| `rm arquivo.txt` | Remove um arquivo. | `rm arquivo.txt` |
| `rmdir nome_da_pasta` | Remove uma pasta vazia. | `rmdir pasta_vazia` |
| `rm -r nome_da_pasta` | Remove uma pasta com todo o seu conteúdo. | `rm -r pasta` |

---

## 3. Visualização de arquivos

| Comando | Descrição | Exemplo |
|---|---|---|
| `cat arquivo.txt` | Mostra todo o conteúdo de um arquivo no terminal. | `cat arquivo.txt` |
| `less arquivo.txt` | Abre um arquivo para leitura página por página. | `less arquivo.txt` |
| `head arquivo.txt` | Mostra as primeiras linhas de um arquivo. | `head arquivo.txt` |
| `head -n 20 arquivo.txt` | Mostra as 20 primeiras linhas de um arquivo. | `head -n 20 arquivo.txt` |
| `tail arquivo.txt` | Mostra as últimas linhas de um arquivo. | `tail arquivo.txt` |
| `tail -f arquivo.log` | Mostra as últimas linhas de um arquivo em tempo real. | `tail -f /var/log/syslog` |

---

## 4. Busca de arquivos e textos

| Comando | Descrição | Exemplo |
|---|---|---|
| `find /caminho -name "arquivo.txt"` | Procura um arquivo pelo nome. | `find /home/usuario -name "arquivo.txt"` |
| `find /caminho -name "*.pdf"` | Procura arquivos por extensão. | `find /home/usuario -name "*.pdf"` |
| `grep "texto" arquivo.txt` | Procura um texto dentro de um arquivo. | `grep "erro" arquivo.log` |
| `grep -r "texto" /caminho` | Procura um texto dentro de vários arquivos em uma pasta. | `grep -r "database" /etc` |
| `grep -i "texto" arquivo.txt` | Procura texto ignorando maiúsculas e minúsculas. | `grep -i "erro" arquivo.log` |

---

## 5. Permissões e propriedade

| Comando | Descrição | Exemplo |
|---|---|---|
| `ls -l` | Mostra permissões, dono, grupo, tamanho e data dos arquivos. | `ls -l` |
| `chmod 755 arquivo.sh` | Altera permissões de um arquivo ou script. | `chmod 755 script.sh` |
| `chmod +x script.sh` | Adiciona permissão de execução a um script. | `chmod +x script.sh` |
| `sudo chown usuario:grupo arquivo` | Altera o dono e o grupo de um arquivo. | `sudo chown douglas:douglas arquivo.txt` |
| `sudo chown -R usuario:grupo pasta` | Altera o dono e o grupo de uma pasta e de todo o seu conteúdo. | `sudo chown -R douglas:douglas projeto` |

---

## 6. Administração de pacotes no Ubuntu/Debian

| Comando | Descrição | Exemplo |
|---|---|---|
| `sudo apt update` | Atualiza a lista de pacotes disponíveis nos repositórios. | `sudo apt update` |
| `sudo apt upgrade -y` | Atualiza os pacotes instalados no sistema. | `sudo apt upgrade -y` |
| `sudo apt install pacote` | Instala um pacote. | `sudo apt install git` |
| `sudo apt remove pacote` | Remove um pacote. | `sudo apt remove git` |
| `apt search pacote` | Pesquisa pacotes disponíveis. | `apt search docker` |
| `sudo apt autoremove` | Remove pacotes instalados automaticamente que não são mais necessários. | `sudo apt autoremove` |

---

## 7. Processos e uso do sistema

| Comando | Descrição | Exemplo |
|---|---|---|
| `ps aux` | Lista processos em execução. | `ps aux` |
| `top` | Monitora processos em tempo real. | `top` |
| `htop` | Monitora processos em tempo real com interface mais amigável, se estiver instalado. | `htop` |
| `kill PID` | Encerra um processo pelo seu PID. | `kill 1234` |
| `kill -9 PID` | Força o encerramento de um processo. | `kill -9 1234` |
| `pkill nome_do_processo` | Encerra processos pelo nome. | `pkill firefox` |

---

## 8. Uso de disco e armazenamento

| Comando | Descrição | Exemplo |
|---|---|---|
| `df -h` | Mostra o espaço utilizado e disponível nos discos. | `df -h` |
| `du -sh nome_da_pasta` | Mostra o tamanho total de uma pasta. | `du -sh Downloads` |
| `du -sh *` | Mostra o tamanho dos itens dentro da pasta atual. | `du -sh *` |
| `lsblk` | Lista discos, partições e pontos de montagem. | `lsblk` |
| `blkid` | Mostra UUID e tipo de sistema de arquivos das partições. | `sudo blkid` |

---

## 9. Montagem de discos

| Comando | Descrição | Exemplo |
|---|---|---|
| `sudo mkdir -p /mnt/hdexterno` | Cria um ponto de montagem para disco ou partição. | `sudo mkdir -p /mnt/hdexterno` |
| `sudo mount /dev/sdb1 /mnt` | Monta uma partição em `/mnt`. | `sudo mount /dev/sdb1 /mnt` |
| `sudo mount /dev/sdb1 /mnt/hdexterno` | Monta uma partição em uma pasta específica. | `sudo mount /dev/sdb1 /mnt/hdexterno` |
| `sudo umount /mnt/hdexterno` | Desmonta uma partição. | `sudo umount /mnt/hdexterno` |

---

## 10. Rede

| Comando | Descrição | Exemplo |
|---|---|---|
| `ip addr` | Mostra interfaces de rede e endereços IP. | `ip addr` |
| `hostname -I` | Mostra o endereço IP da máquina. | `hostname -I` |
| `ping dominio.com` | Testa conectividade com um endereço. | `ping google.com` |
| `ip route` | Mostra as rotas de rede configuradas. | `ip route` |
| `nc -vz dominio.com porta` | Testa se uma porta está aberta em um servidor. | `nc -vz exemplo.com 443` |
| `curl URL` | Faz uma requisição HTTP. | `curl https://example.com` |
| `wget URL` | Baixa um arquivo pela internet. | `wget https://example.com/arquivo.zip` |

---

## 11. Usuários e permissões administrativas

| Comando | Descrição | Exemplo |
|---|---|---|
| `whoami` | Mostra o usuário atual. | `whoami` |
| `sudo comando` | Executa um comando com privilégios administrativos. | `sudo apt update` |
| `sudo su` | Troca para o usuário root. | `sudo su` |
| `sudo adduser nome_usuario` | Cria um novo usuário. | `sudo adduser joao` |
| `sudo passwd nome_usuario` | Altera a senha de um usuário. | `sudo passwd joao` |
| `groups` | Mostra os grupos do usuário atual. | `groups` |

---

## 12. Serviços do sistema

| Comando | Descrição | Exemplo |
|---|---|---|
| `sudo systemctl status nome_servico` | Mostra o status de um serviço. | `sudo systemctl status nginx` |
| `sudo systemctl start nome_servico` | Inicia um serviço. | `sudo systemctl start nginx` |
| `sudo systemctl stop nome_servico` | Para um serviço. | `sudo systemctl stop nginx` |
| `sudo systemctl restart nome_servico` | Reinicia um serviço. | `sudo systemctl restart nginx` |
| `sudo systemctl enable nome_servico` | Habilita um serviço para iniciar junto com o sistema. | `sudo systemctl enable nginx` |
| `sudo systemctl disable nome_servico` | Desabilita a inicialização automática de um serviço. | `sudo systemctl disable nginx` |
| `journalctl -u nome_servico` | Mostra os logs de um serviço. | `journalctl -u nginx` |
| `journalctl -u nome_servico -f` | Mostra os logs de um serviço em tempo real. | `journalctl -u nginx -f` |

---

## 13. Compactação e descompactação

| Comando | Descrição | Exemplo |
|---|---|---|
| `tar -czvf arquivo.tar.gz pasta/` | Compacta uma pasta em formato `.tar.gz`. | `tar -czvf backup.tar.gz projeto/` |
| `tar -xzvf arquivo.tar.gz` | Descompacta um arquivo `.tar.gz`. | `tar -xzvf backup.tar.gz` |
| `zip -r arquivo.zip pasta/` | Compacta uma pasta em formato `.zip`. | `zip -r projeto.zip projeto/` |
| `unzip arquivo.zip` | Descompacta um arquivo `.zip`. | `unzip projeto.zip` |

---

## 14. SSH e acesso remoto

| Comando | Descrição | Exemplo |
|---|---|---|
| `ssh usuario@ip_do_servidor` | Acessa um servidor remoto por SSH. | `ssh ubuntu@192.168.0.10` |
| `ssh -i chave.pem usuario@ip_do_servidor` | Acessa um servidor remoto usando chave SSH. | `ssh -i chave.pem ubuntu@192.168.0.10` |
| `scp arquivo.txt usuario@ip:/caminho/destino` | Copia um arquivo local para um servidor remoto. | `scp arquivo.txt ubuntu@192.168.0.10:/home/ubuntu/` |
| `scp usuario@ip:/caminho/arquivo.txt .` | Copia um arquivo do servidor remoto para a máquina local. | `scp ubuntu@192.168.0.10:/home/ubuntu/arquivo.txt .` |

---

## 15. Histórico e ajuda

| Comando | Descrição | Exemplo |
|---|---|---|
| `history` | Mostra o histórico de comandos executados. | `history` |
| `!123` | Reexecuta um comando pelo número do histórico. | `!123` |
| `man comando` | Abre o manual de um comando. | `man ls` |
| `comando --help` | Mostra ajuda rápida de um comando. | `ls --help` |

---

## 16. Comandos úteis no dia a dia

| Comando | Descrição | Exemplo |
|---|---|---|
| `clear` | Limpa a tela do terminal. | `clear` |
| `date` | Mostra a data e hora atual. | `date` |
| `uptime` | Mostra há quanto tempo a máquina está ligada. | `uptime` |
| `uname -a` | Mostra informações do kernel e do sistema. | `uname -a` |
| `cat /etc/os-release` | Mostra informações da distribuição Linux. | `cat /etc/os-release` |
| `free -h` | Mostra o uso de memória RAM. | `free -h` |
| `sudo reboot` | Reinicia a máquina. | `sudo reboot` |
| `sudo shutdown now` | Desliga a máquina imediatamente. | `sudo shutdown now` |

---

## 17. Tabela geral resumida

| Comando | Função principal |
|---|---|
| `pwd` | Mostra o diretório atual |
| `ls -la` | Lista arquivos com detalhes |
| `cd` | Navega entre diretórios |
| `mkdir` | Cria diretório |
| `touch` | Cria arquivo vazio |
| `cp` | Copia arquivos ou pastas |
| `mv` | Move ou renomeia arquivos |
| `rm` | Remove arquivos |
| `cat` | Mostra conteúdo de arquivo |
| `less` | Visualiza arquivo por páginas |
| `grep` | Busca texto em arquivos |
| `find` | Busca arquivos |
| `chmod` | Altera permissões |
| `chown` | Altera dono |
| `sudo` | Executa como administrador |
| `apt` | Gerencia pacotes no Ubuntu/Debian |
| `ps aux` | Lista processos |
| `top` | Monitora processos |
| `kill` | Encerra processo |
| `df -h` | Mostra espaço em disco |
| `du -sh` | Mostra tamanho de pasta |
| `lsblk` | Lista discos e partições |
| `mount` | Monta partição |
| `umount` | Desmonta partição |
| `ip addr` | Mostra interfaces de rede |
| `ping` | Testa conexão |
| `curl` | Faz requisições HTTP |
| `systemctl` | Gerencia serviços |
| `journalctl` | Consulta logs |
| `tar` | Compacta e descompacta arquivos |
| `ssh` | Acessa servidor remoto |
| `scp` | Copia arquivos via SSH |
| `history` | Mostra histórico |
| `man` | Mostra manual do comando |
