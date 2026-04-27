## Principais distribuições Linux e gerenciadores de pacotes

### 1. Distribuições baseadas em Debian/Ubuntu

Exemplos:

- Debian
- Ubuntu
- Linux Mint
- Pop!_OS
- Elementary OS
- Zorin OS

Essas distribuições utilizam pacotes no formato **`.deb`** e normalmente usam os gerenciadores **dpkg** e **apt**.

---

#### DPKG

O **dpkg** é um gerenciador de pacotes de baixo nível utilizado em distribuições baseadas em Debian. Ele instala, remove e consulta pacotes locais no formato **`.deb`**.

#### Instalar um pacote `.deb`

```bash
sudo dpkg -i pacote.deb
```

Exemplo:

```bash
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

#### Remover um pacote instalado

```bash
sudo dpkg -r pacote
```

Exemplo:

```bash
sudo dpkg -r google-chrome-stable
```

#### Corrigir dependências quebradas

Quando um pacote `.deb` é instalado manualmente, pode ser necessário corrigir dependências:

```bash
sudo apt install -f
```

---

#### APT

O **apt** é o gerenciador de pacotes mais utilizado em distribuições baseadas em Debian/Ubuntu. Ele busca pacotes nos repositórios configurados do sistema e resolve dependências automaticamente.

#### Atualizar a lista de pacotes

```bash
sudo apt update
```

Esse comando atualiza a lista de pacotes disponíveis nos repositórios.

#### Atualizar os pacotes instalados

```bash
sudo apt upgrade -y
```

Esse comando atualiza os pacotes já instalados no sistema.

#### Instalar um pacote

```bash
sudo apt install pacote
```

Exemplo:

```bash
sudo apt install git
```

#### Remover um pacote

```bash
sudo apt remove pacote
```

Exemplo:

```bash
sudo apt remove git
```

#### Pesquisar um pacote

```bash
sudo apt search pacote
```

Exemplo:

```bash
sudo apt search docker
```

#### Remover pacotes desnecessários

```bash
sudo apt autoremove
```

---

### 2. Distribuições baseadas em Red Hat/Fedora

Exemplos:

- Fedora
- Red Hat Enterprise Linux
- Rocky Linux
- AlmaLinux
- CentOS Stream

Essas distribuições utilizam pacotes no formato **`.rpm`** e normalmente usam os gerenciadores **dnf**, **yum** e **rpm**.

---

#### DNF

O **dnf** é o gerenciador de pacotes atual utilizado em distribuições como Fedora, Rocky Linux, AlmaLinux e versões recentes do Red Hat Enterprise Linux.

#### Atualizar os pacotes do sistema

```bash
sudo dnf update -y
```

#### Instalar um pacote

```bash
sudo dnf install pacote
```

Exemplo:

```bash
sudo dnf install git
```

#### Remover um pacote

```bash
sudo dnf remove pacote
```

Exemplo:

```bash
sudo dnf remove git
```

#### Pesquisar um pacote

```bash
sudo dnf search pacote
```

Exemplo:

```bash
sudo dnf search docker
```

---

#### RPM

O **rpm** é um gerenciador de baixo nível para pacotes no formato **`.rpm`**.

#### Instalar um pacote `.rpm`

```bash
sudo rpm -i pacote.rpm
```

#### Atualizar ou instalar um pacote `.rpm`

```bash
sudo rpm -Uvh pacote.rpm
```

#### Remover um pacote

```bash
sudo rpm -e pacote
```

#### Listar pacotes instalados

```bash
rpm -qa
```

---

### 3. Distribuições baseadas em Arch Linux

Exemplos:

- Arch Linux
- Manjaro
- EndeavourOS
- Garuda Linux

Essas distribuições utilizam o gerenciador de pacotes **pacman**.

---

#### Pacman

O **pacman** é o gerenciador de pacotes padrão do Arch Linux e de distribuições derivadas.

#### Atualizar o sistema

```bash
sudo pacman -Syu
```

#### Instalar um pacote

```bash
sudo pacman -S pacote
```

Exemplo:

```bash
sudo pacman -S git
```

#### Remover um pacote

```bash
sudo pacman -R pacote
```

Exemplo:

```bash
sudo pacman -R git
```

#### Remover pacote e dependências não utilizadas

```bash
sudo pacman -Rns pacote
```

#### Pesquisar um pacote

```bash
pacman -Ss pacote
```

Exemplo:

```bash
pacman -Ss docker
```

---

### 4. Distribuições baseadas em openSUSE

Exemplos:

- openSUSE Leap
- openSUSE Tumbleweed
- SUSE Linux Enterprise

Essas distribuições utilizam o gerenciador de pacotes **zypper**.

---

#### Zypper

O **zypper** é o gerenciador de pacotes utilizado em distribuições SUSE e openSUSE.

#### Atualizar os repositórios

```bash
sudo zypper refresh
```

#### Atualizar o sistema

```bash
sudo zypper update
```

#### Instalar um pacote

```bash
sudo zypper install pacote
```

Exemplo:

```bash
sudo zypper install git
```

#### Remover um pacote

```bash
sudo zypper remove pacote
```

#### Pesquisar um pacote

```bash
zypper search pacote
```

---

### 5. Distribuições baseadas em Alpine Linux

Exemplos:

- Alpine Linux
- Containers baseados em Alpine

O Alpine Linux utiliza o gerenciador de pacotes **apk**.

---

#### APK

O **apk** é o gerenciador de pacotes utilizado pelo Alpine Linux.

#### Atualizar a lista de pacotes

```bash
sudo apk update
```

#### Atualizar pacotes instalados

```bash
sudo apk upgrade
```

#### Instalar um pacote

```bash
sudo apk add pacote
```

Exemplo:

```bash
sudo apk add git
```

#### Remover um pacote

```bash
sudo apk del pacote
```

#### Pesquisar um pacote

```bash
apk search pacote
```

---

#### Tabela resumo

| Família Linux | Distribuições | Formato de pacote | Gerenciador principal |
|---|---|---|---|
| Debian/Ubuntu | Debian, Ubuntu, Mint, Pop!_OS, Zorin OS | `.deb` | `apt` |
| Debian/Ubuntu | Debian, Ubuntu, Mint | `.deb` | `dpkg` |
| Red Hat/Fedora | Fedora, RHEL, Rocky, AlmaLinux | `.rpm` | `dnf` |
| Red Hat/Fedora | Fedora, RHEL, Rocky, AlmaLinux | `.rpm` | `rpm` |
| Arch Linux | Arch, Manjaro, EndeavourOS | Pacotes Arch | `pacman` |
| openSUSE/SUSE | openSUSE, SUSE Linux Enterprise | `.rpm` | `zypper` |
| Alpine Linux | Alpine | `.apk` | `apk` |

---

### Comandos principais por distribuição

#### Debian/Ubuntu

```bash
sudo apt update
sudo apt upgrade -y
sudo apt install pacote
sudo apt remove pacote
sudo apt search pacote
```

#### Instalação manual com DPKG

```bash
sudo dpkg -i pacote.deb
sudo dpkg -r pacote
sudo apt install -f
```

#### Fedora/Rocky/AlmaLinux

```bash
sudo dnf update -y
sudo dnf install pacote
sudo dnf remove pacote
sudo dnf search pacote
```

#### Arch/Manjaro

```bash
sudo pacman -Syu
sudo pacman -S pacote
sudo pacman -R pacote
pacman -Ss pacote
```

#### openSUSE

```bash
sudo zypper refresh
sudo zypper update
sudo zypper install pacote
sudo zypper remove pacote
zypper search pacote
```

#### Alpine

```bash
sudo apk update
sudo apk upgrade
sudo apk add pacote
sudo apk del pacote
apk search pacote
```

### Sistema de arquivos em Linux

No Linux, o sistema de arquivos é organizado em uma estrutura hierárquica, parecida com uma árvore. Tudo começa no diretório raiz, representado por:

```bash
/
```

A partir dele ficam todos os demais diretórios, arquivos, dispositivos, programas, configurações e dados do sistema.

---

### 1. Visão geral da estrutura

```bash
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

---

### 2. Principais diretórios do Linux

#### `/`

É o diretório raiz do sistema. Todos os arquivos e diretórios do Linux ficam abaixo dele.

Exemplo:

```bash
cd /
ls
```

---

#### `/home`

Armazena os arquivos pessoais dos usuários comuns do sistema.

Exemplos:

```bash
/home/douglas
/home/maria
/home/joao
```

Normalmente contém pastas como:

```bash
Documentos
Downloads
Imagens
Vídeos
Área de Trabalho
```

Exemplo de uso:

```bash
cd /home/douglas
```

---

#### `/root`

É o diretório pessoal do usuário administrador, chamado **root**.

Não deve ser confundido com o diretório `/`.

```bash
/root
```

Diferença importante:

```bash
/       # raiz do sistema
/root   # pasta pessoal do usuário root
```

---

#### `/etc`

Armazena arquivos de configuração do sistema e de serviços instalados.

Exemplos:

```bash
/etc/hosts
/etc/fstab
/etc/ssh/sshd_config
/etc/nginx/nginx.conf
```

É uma pasta muito importante para administração do Linux.

---

#### `/bin`

Contém comandos essenciais disponíveis para todos os usuários.

Exemplos:

```bash
ls
cp
mv
rm
cat
mkdir
```

Exemplo:

```bash
/bin/ls
```

---

#### `/sbin`

Contém comandos administrativos essenciais, geralmente usados pelo root ou com `sudo`.

Exemplos:

```bash
reboot
shutdown
fdisk
mount
iptables
```

---

#### `/usr`

Armazena programas, bibliotecas, documentação e arquivos compartilhados instalados no sistema.

Subdiretórios comuns:

```bash
/usr/bin
/usr/sbin
/usr/lib
/usr/share
/usr/local
```

Exemplos:

```bash
/usr/bin/python3
/usr/bin/git
```

---

#### `/usr/bin`

Contém a maioria dos comandos e programas instalados pelo sistema.

Exemplos:

```bash
python3
git
docker
vim
nano
curl
```

---

#### `/usr/local`

Usado para programas instalados manualmente pelo administrador do sistema.

Exemplo:

```bash
/usr/local/bin
```

É comum encontrar comandos personalizados nesse diretório.

---

#### `/var`

Armazena arquivos variáveis, ou seja, arquivos que mudam com frequência.

Exemplos:

```bash
/var/log
/var/www
/var/cache
/var/lib
/var/spool
```

Uso comum:

```bash
/var/log      # logs do sistema
/var/www      # arquivos de sites
/var/lib      # dados de serviços
```

---

#### `/var/log`

Armazena logs do sistema e de aplicações.

Exemplos:

```bash
/var/log/syslog
/var/log/auth.log
/var/log/nginx/access.log
/var/log/nginx/error.log
```

Comando útil:

```bash
tail -f /var/log/syslog
```

---

#### `/tmp`

Armazena arquivos temporários.

Normalmente, os arquivos nessa pasta podem ser apagados automaticamente pelo sistema.

Exemplo:

```bash
/tmp
```

---

#### `/boot`

Contém arquivos necessários para inicialização do sistema.

Exemplos:

```bash
vmlinuz
initrd.img
grub
```

É onde ficam arquivos do kernel e do bootloader.

---

#### `/dev`

Representa dispositivos do sistema como arquivos.

Exemplos:

```bash
/dev/sda
/dev/sda1
/dev/nvme0n1
/dev/tty
/dev/null
```

No Linux, dispositivos como discos, partições, terminais e portas são acessados como arquivos.

---

#### `/mnt`

Usado normalmente para montagem manual de discos, partições ou compartilhamentos de rede.

Exemplo:

```bash
sudo mount /dev/sdb1 /mnt/hdexterno
```

---

#### `/media`

Usado para montagem automática de dispositivos removíveis, como pendrives e HDs externos.

Exemplos:

```bash
/media/douglas/PENDRIVE
/media/douglas/HD_EXTERNO
```

Em ambientes gráficos, o Ubuntu costuma montar dispositivos removíveis dentro de `/media/usuario`.

---

#### `/proc`

É um sistema de arquivos virtual que apresenta informações do kernel e dos processos em execução.

Exemplos:

```bash
/proc/cpuinfo
/proc/meminfo
/proc/1
```

Comandos úteis:

```bash
cat /proc/cpuinfo
cat /proc/meminfo
```

---

#### `/sys`

Também é um sistema de arquivos virtual. Ele expõe informações sobre dispositivos, drivers e kernel.

Exemplo:

```bash
/sys/class
/sys/block
/sys/module
```

---

#### `/run`

Armazena arquivos temporários de execução criados desde o boot atual.

Exemplos:

```bash
/run
/run/user
/run/systemd
```

É usado por serviços e processos em execução.

---

#### `/opt`

Usado para instalação de softwares opcionais ou de terceiros.

Exemplos:

```bash
/opt/google
/opt/bookstack
/opt/app
```

Em servidores, é comum instalar aplicações próprias dentro de `/opt`.

---

#### `/srv`

Pode armazenar dados servidos pelo sistema, como sites, FTP ou aplicações.

Exemplos:

```bash
/srv/www
/srv/ftp
```

---

#### `/lib` e `/lib64`

Contêm bibliotecas essenciais usadas por comandos e programas do sistema.

Exemplos:

```bash
/lib
/lib64
```

São importantes para o funcionamento do sistema operacional.

---

### 3. Caminhos absolutos e relativos

#### Caminho absoluto

É o caminho completo a partir da raiz `/`.

Exemplo:

```bash
/home/douglas/Documentos/arquivo.txt
```

#### Caminho relativo

É o caminho a partir do diretório atual.

Exemplo:

```bash
Documentos/arquivo.txt
```

Se você estiver em:

```bash
/home/douglas
```

Então o caminho relativo:

```bash
Documentos/arquivo.txt
```

equivale a:

```bash
/home/douglas/Documentos/arquivo.txt
```

---

### 4. Diretório atual e diretório anterior

#### Ver o diretório atual

```bash
pwd
```

#### Ir para outro diretório

```bash
cd /home/douglas
```

#### Voltar um nível

```bash
cd ..
```

### Ir para a home do usuário

```bash
cd ~
```

ou:

```bash
cd
```

#### Ir para o diretório raiz

```bash
cd /
```

---

### 5. Permissões no Linux

Cada arquivo e diretório possui permissões para três grupos:

```bash
usuário dono
grupo
outros usuários
```

As permissões principais são:

```bash
r = read    # leitura
w = write   # escrita
x = execute # execução
```

Exemplo de permissões:

```bash
-rw-r--r--
```

Interpretação:

```bash
-     arquivo comum
rw-   dono pode ler e escrever
r--   grupo pode apenas ler
r--   outros podem apenas ler
```

Exemplo para diretório:

```bash
drwxr-xr-x
```

Interpretação:

```bash
d     diretório
rwx   dono pode ler, escrever e acessar
r-x   grupo pode ler e acessar
r-x   outros podem ler e acessar
```

---

### 6. Comandos básicos para navegar e manipular arquivos

#### Listar arquivos

```bash
ls
```

Listar com detalhes:

```bash
ls -la
```

#### Criar diretório

```bash
mkdir nome_da_pasta
```

#### Criar arquivo vazio

```bash
touch arquivo.txt
```

#### Copiar arquivo

```bash
cp origem destino
```

Exemplo:

```bash
cp arquivo.txt /home/douglas/Documentos/
```

#### Mover ou renomear arquivo

```bash
mv origem destino
```

Exemplo para mover:

```bash
mv arquivo.txt /home/douglas/Documentos/
```

Exemplo para renomear:

```bash
mv antigo.txt novo.txt
```

#### Remover arquivo

```bash
rm arquivo.txt
```

#### Remover diretório vazio

```bash
rmdir pasta
```

#### Remover diretório com conteúdo

```bash
rm -r pasta
```

Use com cuidado.

---

### 7. Tipos comuns de arquivos no Linux

| Símbolo | Tipo |
|---|---|
| `-` | Arquivo comum |
| `d` | Diretório |
| `l` | Link simbólico |
| `b` | Dispositivo de bloco |
| `c` | Dispositivo de caractere |
| `s` | Socket |
| `p` | Pipe |

Exemplo:

```bash
ls -l
```

Saída:

```bash
drwxr-xr-x  2 douglas douglas 4096 abr 27  Documentos
-rw-r--r--  1 douglas douglas 1200 abr 27  arquivo.txt
lrwxrwxrwx  1 root    root      11 abr 27  link -> arquivo.txt
```

---

### 8. Sistemas de arquivos comuns

Linux pode usar vários tipos de sistemas de arquivos.

| Sistema de arquivos | Uso comum |
|---|---|
| `ext4` | Muito comum em instalações Linux |
| `xfs` | Muito usado em servidores |
| `btrfs` | Suporta snapshots e recursos avançados |
| `swap` | Área de troca de memória |
| `vfat` | Pendrives e partições EFI |
| `exfat` | HDs externos e pendrives grandes |
| `ntfs` | Discos do Windows |
| `nfs` | Compartilhamento de rede Linux/Unix |

---

### 9. Montagem de discos

No Linux, discos e partições precisam estar montados em algum diretório para serem acessados.

Exemplo de dispositivo:

```bash
/dev/sdb1
```

Exemplo de ponto de montagem:

```bash
/mnt/hdexterno
```

Comando de montagem:

```bash
sudo mount /dev/sdb1 /mnt/hdexterno
```

Para desmontar:

```bash
sudo umount /mnt/hdexterno
```

---

### 10. Arquivo `/etc/fstab`

O arquivo `/etc/fstab` define montagens automáticas de discos e partições durante a inicialização do sistema.

Exemplo:

```bash
UUID=xxxx-xxxx /mnt/dados ext4 defaults 0 2
```

Campos principais:

```bash
UUID do disco
ponto de montagem
tipo do sistema de arquivos
opções
dump
fsck
```

Antes de editar esse arquivo, é importante fazer backup:

```bash
sudo cp /etc/fstab /etc/fstab.bkp
```

---

### 11. Resumo prático

| Diretório | Função principal |
|---|---|
| `/` | Raiz do sistema |
| `/home` | Arquivos dos usuários |
| `/root` | Pasta pessoal do administrador |
| `/etc` | Configurações do sistema |
| `/bin` | Comandos essenciais |
| `/sbin` | Comandos administrativos |
| `/usr` | Programas e arquivos compartilhados |
| `/var` | Logs, caches e dados variáveis |
| `/tmp` | Arquivos temporários |
| `/boot` | Arquivos de inicialização |
| `/dev` | Dispositivos do sistema |
| `/mnt` | Montagens manuais |
| `/media` | Montagens automáticas de pendrives e HDs |
| `/proc` | Informações virtuais de processos e kernel |
| `/sys` | Informações virtuais de hardware e kernel |
| `/opt` | Softwares opcionais ou aplicações próprias |
| `/srv` | Dados servidos por serviços |

---

### 12. Exemplo prático de navegação

```bash
cd /
ls
cd /home
ls
cd douglas
pwd
ls -la
```

Esse fluxo acessa a raiz do sistema, entra na pasta dos usuários, acessa a pasta do usuário `douglas`, mostra o caminho atual e lista os arquivos com detalhes.

### Tabela de principais comandos Linux

Este documento reúne os principais comandos Linux em formato de tabela, organizados por categoria, com descrição e exemplo de uso.

---

#### 1. Navegação entre diretórios

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

#### 2. Manipulação de arquivos e pastas

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

#### 3. Visualização de arquivos

| Comando | Descrição | Exemplo |
|---|---|---|
| `cat arquivo.txt` | Mostra todo o conteúdo de um arquivo no terminal. | `cat arquivo.txt` |
| `less arquivo.txt` | Abre um arquivo para leitura página por página. | `less arquivo.txt` |
| `head arquivo.txt` | Mostra as primeiras linhas de um arquivo. | `head arquivo.txt` |
| `head -n 20 arquivo.txt` | Mostra as 20 primeiras linhas de um arquivo. | `head -n 20 arquivo.txt` |
| `tail arquivo.txt` | Mostra as últimas linhas de um arquivo. | `tail arquivo.txt` |
| `tail -f arquivo.log` | Mostra as últimas linhas de um arquivo em tempo real. | `tail -f /var/log/syslog` |

---

#### 4. Busca de arquivos e textos

| Comando | Descrição | Exemplo |
|---|---|---|
| `find /caminho -name "arquivo.txt"` | Procura um arquivo pelo nome. | `find /home/usuario -name "arquivo.txt"` |
| `find /caminho -name "*.pdf"` | Procura arquivos por extensão. | `find /home/usuario -name "*.pdf"` |
| `grep "texto" arquivo.txt` | Procura um texto dentro de um arquivo. | `grep "erro" arquivo.log` |
| `grep -r "texto" /caminho` | Procura um texto dentro de vários arquivos em uma pasta. | `grep -r "database" /etc` |
| `grep -i "texto" arquivo.txt` | Procura texto ignorando maiúsculas e minúsculas. | `grep -i "erro" arquivo.log` |

---

#### 5. Permissões e propriedade

| Comando | Descrição | Exemplo |
|---|---|---|
| `ls -l` | Mostra permissões, dono, grupo, tamanho e data dos arquivos. | `ls -l` |
| `chmod 755 arquivo.sh` | Altera permissões de um arquivo ou script. | `chmod 755 script.sh` |
| `chmod +x script.sh` | Adiciona permissão de execução a um script. | `chmod +x script.sh` |
| `sudo chown usuario:grupo arquivo` | Altera o dono e o grupo de um arquivo. | `sudo chown douglas:douglas arquivo.txt` |
| `sudo chown -R usuario:grupo pasta` | Altera o dono e o grupo de uma pasta e de todo o seu conteúdo. | `sudo chown -R douglas:douglas projeto` |

---

#### 6. Administração de pacotes no Ubuntu/Debian

| Comando | Descrição | Exemplo |
|---|---|---|
| `sudo apt update` | Atualiza a lista de pacotes disponíveis nos repositórios. | `sudo apt update` |
| `sudo apt upgrade -y` | Atualiza os pacotes instalados no sistema. | `sudo apt upgrade -y` |
| `sudo apt install pacote` | Instala um pacote. | `sudo apt install git` |
| `sudo apt remove pacote` | Remove um pacote. | `sudo apt remove git` |
| `apt search pacote` | Pesquisa pacotes disponíveis. | `apt search docker` |
| `sudo apt autoremove` | Remove pacotes instalados automaticamente que não são mais necessários. | `sudo apt autoremove` |

---

#### 7. Processos e uso do sistema

| Comando | Descrição | Exemplo |
|---|---|---|
| `ps aux` | Lista processos em execução. | `ps aux` |
| `top` | Monitora processos em tempo real. | `top` |
| `htop` | Monitora processos em tempo real com interface mais amigável, se estiver instalado. | `htop` |
| `kill PID` | Encerra um processo pelo seu PID. | `kill 1234` |
| `kill -9 PID` | Força o encerramento de um processo. | `kill -9 1234` |
| `pkill nome_do_processo` | Encerra processos pelo nome. | `pkill firefox` |

---

#### 8. Uso de disco e armazenamento

| Comando | Descrição | Exemplo |
|---|---|---|
| `df -h` | Mostra o espaço utilizado e disponível nos discos. | `df -h` |
| `du -sh nome_da_pasta` | Mostra o tamanho total de uma pasta. | `du -sh Downloads` |
| `du -sh *` | Mostra o tamanho dos itens dentro da pasta atual. | `du -sh *` |
| `lsblk` | Lista discos, partições e pontos de montagem. | `lsblk` |
| `blkid` | Mostra UUID e tipo de sistema de arquivos das partições. | `sudo blkid` |

---

#### 9. Montagem de discos

| Comando | Descrição | Exemplo |
|---|---|---|
| `sudo mkdir -p /mnt/hdexterno` | Cria um ponto de montagem para disco ou partição. | `sudo mkdir -p /mnt/hdexterno` |
| `sudo mount /dev/sdb1 /mnt` | Monta uma partição em `/mnt`. | `sudo mount /dev/sdb1 /mnt` |
| `sudo mount /dev/sdb1 /mnt/hdexterno` | Monta uma partição em uma pasta específica. | `sudo mount /dev/sdb1 /mnt/hdexterno` |
| `sudo umount /mnt/hdexterno` | Desmonta uma partição. | `sudo umount /mnt/hdexterno` |

---

#### 10. Rede

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

#### 11. Usuários e permissões administrativas

| Comando | Descrição | Exemplo |
|---|---|---|
| `whoami` | Mostra o usuário atual. | `whoami` |
| `sudo comando` | Executa um comando com privilégios administrativos. | `sudo apt update` |
| `sudo su` | Troca para o usuário root. | `sudo su` |
| `sudo adduser nome_usuario` | Cria um novo usuário. | `sudo adduser joao` |
| `sudo passwd nome_usuario` | Altera a senha de um usuário. | `sudo passwd joao` |
| `groups` | Mostra os grupos do usuário atual. | `groups` |

---

#### 12. Serviços do sistema

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

#### 13. Compactação e descompactação

| Comando | Descrição | Exemplo |
|---|---|---|
| `tar -czvf arquivo.tar.gz pasta/` | Compacta uma pasta em formato `.tar.gz`. | `tar -czvf backup.tar.gz projeto/` |
| `tar -xzvf arquivo.tar.gz` | Descompacta um arquivo `.tar.gz`. | `tar -xzvf backup.tar.gz` |
| `zip -r arquivo.zip pasta/` | Compacta uma pasta em formato `.zip`. | `zip -r projeto.zip projeto/` |
| `unzip arquivo.zip` | Descompacta um arquivo `.zip`. | `unzip projeto.zip` |

---

#### 14. SSH e acesso remoto

| Comando | Descrição | Exemplo |
|---|---|---|
| `ssh usuario@ip_do_servidor` | Acessa um servidor remoto por SSH. | `ssh ubuntu@192.168.0.10` |
| `ssh -i chave.pem usuario@ip_do_servidor` | Acessa um servidor remoto usando chave SSH. | `ssh -i chave.pem ubuntu@192.168.0.10` |
| `scp arquivo.txt usuario@ip:/caminho/destino` | Copia um arquivo local para um servidor remoto. | `scp arquivo.txt ubuntu@192.168.0.10:/home/ubuntu/` |
| `scp usuario@ip:/caminho/arquivo.txt .` | Copia um arquivo do servidor remoto para a máquina local. | `scp ubuntu@192.168.0.10:/home/ubuntu/arquivo.txt .` |

---

#### 15. Histórico e ajuda

| Comando | Descrição | Exemplo |
|---|---|---|
| `history` | Mostra o histórico de comandos executados. | `history` |
| `!123` | Reexecuta um comando pelo número do histórico. | `!123` |
| `man comando` | Abre o manual de um comando. | `man ls` |
| `comando --help` | Mostra ajuda rápida de um comando. | `ls --help` |

---

#### 16. Comandos úteis no dia a dia

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

#### 17. Tabela geral resumida

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

#### 18. Resumo dos redirecionamentos

| Comando | Função | Exemplo |
|---|---|---|
| `comando > saida.txt` | Salva a saída normal em um arquivo, sobrescrevendo o conteúdo anterior. | `ls -la > saida.txt` |
| `comando >> saida.txt` | Adiciona a saída normal ao final de um arquivo, sem apagar o conteúdo anterior. | `ls -la >> saida.txt` |
| `comando 2> erros.txt` | Salva somente os erros em um arquivo, sobrescrevendo o conteúdo anterior. | `ls /pasta/inexistente 2> erros.txt` |
| `comando 2>> erros.txt` | Adiciona somente os erros ao final de um arquivo. | `ls /pasta/inexistente 2>> erros.txt` |
| `comando > saida.txt 2> erros.txt` | Salva a saída normal em um arquivo e os erros em outro arquivo separado. | `find / -name "*.log" > saida.txt 2> erros.txt` |
| `comando > resultado.txt 2>&1` | Salva a saída normal e os erros no mesmo arquivo. | `find / -name "*.log" > resultado.txt 2>&1` |
| `comando >> resultado.txt 2>&1` | Adiciona a saída normal e os erros ao final do mesmo arquivo. | `find / -name "*.log" >> resultado.txt 2>&1` |
| `comando &> resultado.txt` | Salva a saída normal e os erros no mesmo arquivo. Forma curta suportada no Bash. | `find / -name "*.log" &> resultado.txt` |
| `comando 2> /dev/null` | Ignora somente os erros. | `find / -name "*.log" 2> /dev/null` |
| `comando > /dev/null` | Ignora somente a saída normal e mantém os erros no terminal. | `find / -name "*.log" > /dev/null` |
| `comando > /dev/null 2>&1` | Ignora a saída normal e os erros. | `find / -name "*.log" > /dev/null 2>&1` |

---

#### 19. Resumo do `grep`

| Comando | Função | Exemplo |
|---|---|---|
| `grep "texto" arquivo.txt` | Procura um texto dentro de um arquivo. | `grep "erro" arquivo.log` |
| `grep -i "texto" arquivo.txt` | Procura um texto ignorando maiúsculas e minúsculas. | `grep -i "erro" arquivo.log` |
| `grep -n "texto" arquivo.txt` | Mostra o número da linha onde o texto foi encontrado. | `grep -n "erro" arquivo.log` |
| `grep -r "texto" pasta/` | Procura um texto de forma recursiva dentro de uma pasta. | `grep -r "erro" /var/log` |
| `grep -rin "texto" pasta/` | Busca recursivamente, ignora maiúsculas/minúsculas e mostra número da linha. | `grep -rin "erro" .` |
| `grep -v "texto" arquivo.txt` | Mostra as linhas que não contêm o texto pesquisado. | `grep -v "sucesso" arquivo.log` |
| `grep -w "texto" arquivo.txt` | Procura a palavra exata. | `grep -w "erro" arquivo.log` |
| `grep -c "texto" arquivo.txt` | Conta quantas linhas contêm o texto pesquisado. | `grep -c "erro" arquivo.log` |
| `grep -l "texto" *.log` | Mostra apenas os nomes dos arquivos que contêm o texto pesquisado. | `grep -l "erro" *.log` |
| `grep -E "texto1|texto2" arquivo.txt` | Procura múltiplos padrões usando expressão regular estendida. | `grep -E "erro|falha" arquivo.log` |
| `grep -Ei "texto1|texto2" arquivo.txt` | Procura múltiplos padrões ignorando maiúsculas e minúsculas. | `grep -Ei "erro|falha|error|failed" arquivo.log` |
| `grep -A 3 "texto" arquivo.txt` | Mostra a linha encontrada e 3 linhas depois. | `grep -A 3 "erro" arquivo.log` |
| `grep -B 3 "texto" arquivo.txt` | Mostra 3 linhas antes da linha encontrada. | `grep -B 3 "erro" arquivo.log` |
| `grep -C 3 "texto" arquivo.txt` | Mostra 3 linhas antes e 3 linhas depois da linha encontrada. | `grep -C 3 "erro" arquivo.log` |
| `grep --include="*.log" -r "texto" pasta/` | Busca recursivamente apenas em arquivos com determinada extensão. | `grep --include="*.log" -r "erro" /var/log` |
| `grep --exclude="*.zip" -r "texto" pasta/` | Ignora arquivos com determinada extensão durante a busca. | `grep --exclude="*.zip" -r "erro" .` |
| `grep --exclude-dir=".git" -r "texto" pasta/` | Ignora um diretório específico durante a busca. | `grep --exclude-dir=".git" -r "erro" .` |

---

#### 20. Combinações de `grep` com redirecionamento

| Comando | Função | Exemplo |
|---|---|---|
| `grep "texto" arquivo > resultado.txt` | Salva o resultado da busca em um arquivo. | `grep "erro" app.log > resultado.txt` |
| `grep "texto" arquivo >> resultado.txt` | Adiciona o resultado da busca ao final de um arquivo. | `grep "erro" app.log >> resultado.txt` |
| `grep -n "texto" arquivo > resultado.txt` | Salva o resultado com número da linha. | `grep -n "erro" app.log > erros_com_linha.txt` |
| `grep -r "texto" pasta > resultado.txt` | Salva o resultado de uma busca recursiva. | `grep -r "erro" /var/log > resultado_logs.txt` |
| `grep -r "texto" pasta 2> erros.txt` | Salva somente os erros da execução do `grep`. | `grep -r "erro" /var/log 2> erros.txt` |
| `grep -r "texto" pasta > resultado.txt 2> erros.txt` | Salva os resultados encontrados e os erros em arquivos separados. | `grep -r "erro" /var/log > resultado.txt 2> erros.txt` |
| `grep -r "texto" pasta > resultado.txt 2>&1` | Salva os resultados encontrados e os erros no mesmo arquivo. | `grep -r "erro" /var/log > resultado_completo.txt 2>&1` |
| `grep -r "texto" pasta 2> /dev/null` | Executa a busca ocultando erros, como mensagens de permissão negada. | `grep -r "erro" /var/log 2> /dev/null` |
| `grep -rinEi "p1|p2|p3" . > relatorio.txt` | Gera um relatório de busca recursiva com múltiplos termos. | `grep -rinEi "error|erro|failed|falha|exception|timeout" . > relatorio_erros.txt` |
| `grep -rinEi "p1|p2|p3" . > relatorio.txt 2> erros_execucao.txt` | Gera um relatório de ocorrências e salva erros de execução separadamente. | `grep -rinEi "error|erro|failed|falha|exception|timeout" . > relatorio_erros.txt 2> erros_execucao.txt` |
| `grep -rinEi "p1|p2|p3" . > relatorio_completo.txt 2>&1` | Gera um relatório completo com resultados e erros no mesmo arquivo. | `grep -rinEi "error|erro|failed|falha|exception|timeout" . > relatorio_completo.txt 2>&1` |

---

#### 21. Exemplos práticos

| Situação | Comando |
|---|---|
| Procurar erros em um arquivo de log. | `grep -i "error" app.log` |
| Procurar erros e salvar em `.txt`. | `grep -i "error" app.log > erros.txt` |
| Procurar erros com número da linha. | `grep -ni "error" app.log` |
| Procurar múltiplos termos de erro. | `grep -Ei "error|failed|exception|timeout" app.log` |
| Procurar múltiplos termos e salvar em arquivo. | `grep -Ei "error|failed|exception|timeout" app.log > erros.txt` |
| Buscar erros em todos os arquivos da pasta atual. | `grep -rinEi "error|erro|failed|falha|exception|timeout" .` |
| Buscar erros e ignorar mensagens de permissão. | `grep -rinEi "error|erro|failed|falha|exception|timeout" . 2> /dev/null` |
| Buscar erros e salvar resultados e erros separados. | `grep -rinEi "error|erro|failed|falha|exception|timeout" . > resultado.txt 2> erros_execucao.txt` |
| Buscar erros e salvar tudo em um único arquivo. | `grep -rinEi "error|erro|failed|falha|exception|timeout" . > resultado_completo.txt 2>&1` |
| Filtrar logs em tempo real. | `tail -f app.log | grep -i "error"` |
| Filtrar logs em tempo real e salvar. | `tail -f app.log | grep -i "error" > erros_tempo_real.txt` |
| Filtrar logs de serviço com `journalctl`. | `journalctl -u nginx --since "today" | grep -Ei "error|failed|timeout"` |
| Filtrar logs de container Docker. | `docker logs nome_container | grep -Ei "error|failed|exception"` |
| Filtrar logs de container em tempo real. | `docker logs -f nome_container | grep -Ei "error|failed|exception"` |

---

#### 22. Comando recomendado para investigação de erros

```bash
grep -rinEi "error|erro|failed|falha|exception|timeout|refused" . > relatorio_erros.txt 2> erros_execucao.txt
```

#### Explicação

| Parte | Função |
|---|---|
| `grep` | Comando usado para buscar texto. |
| `-r` | Busca recursivamente nas pastas. |
| `-i` | Ignora maiúsculas e minúsculas. |
| `-n` | Mostra o número da linha. |
| `-E` | Permite usar múltiplos padrões com `|`. |
| `"error|erro|failed|falha|exception|timeout|refused"` | Termos pesquisados. |
| `.` | Busca a partir da pasta atual. |
| `> relatorio_erros.txt` | Salva os resultados encontrados. |
| `2> erros_execucao.txt` | Salva erros de execução, como permissão negada. |

### Pontos de montagem no Linux

No Linux, um **ponto de montagem** é um diretório usado para acessar o conteúdo de uma partição, disco, pendrive, HD externo, SSD, compartilhamento de rede ou outro sistema de arquivos.

Diferente do Windows, que usa letras como `C:`, `D:` e `E:`, o Linux integra tudo dentro da árvore principal de diretórios, iniciada em:

```bash
/
```

Exemplos de pontos de montagem:

```bash
/mnt/hdexterno
/media/douglas/PENDRIVE
/home
/boot/efi
/var/lib/docker
```

---

#### 1. O que significa montar um disco

Montar um disco significa conectar uma partição a uma pasta do sistema.

```bash
sudo mount /dev/sdb1 /mnt/hdexterno
```

| Parte | Significado |
|---|---|
| `/dev/sdb1` | Partição que será montada |
| `/mnt/hdexterno` | Diretório onde o conteúdo ficará acessível |
| `mount` | Comando usado para montar |
| `sudo` | Executa com permissão administrativa |

Após a montagem, os arquivos da partição ficam acessíveis em:

```bash
/mnt/hdexterno
```

---

#### 2. Diretórios comuns usados como pontos de montagem

| Diretório | Uso principal |
|---|---|
| `/mnt` | Montagens manuais, temporárias ou configuradas pelo administrador |
| `/media` | Montagens automáticas feitas pela interface gráfica |
| `/home` | Pode ser usado como partição separada para arquivos dos usuários |
| `/boot` | Pode armazenar arquivos de inicialização em partição separada |
| `/boot/efi` | Ponto de montagem da partição EFI em sistemas UEFI |
| `/var` | Pode ser partição separada em servidores, pois armazena logs, caches e dados |
| `/var/lib/docker` | Local comum de dados do Docker |
| `/srv` | Dados servidos por serviços, como sites ou FTP |

---

#### 3. Como ver os pontos de montagem atuais

#### Listar discos, partições e pontos de montagem

```bash
lsblk
```

A coluna mais importante é:

```bash
MOUNTPOINTS
```

---

#### Ver espaço usado e disponível

```bash
df -h
```

---

#### Ver árvore de montagens

```bash
findmnt
```

Consultar um ponto específico:

```bash
findmnt /mnt/hdexterno
```

---

#### Ver montagens ativas

```bash
mount
```

Filtrar uma montagem específica:

```bash
mount | grep sdb1
```

---

#### 4. Como identificar discos e partições

#### Listar discos

```bash
lsblk
```

#### Ver UUID e tipo do sistema de arquivos

```bash
sudo blkid
```

Exemplo de saída:

```bash
/dev/sdb1: UUID="A1B2-C3D4" TYPE="exfat" PARTUUID="12345678-01"
```

| Campo | Significado |
|---|---|
| `/dev/sdb1` | Nome da partição |
| `UUID` | Identificador único da partição |
| `TYPE` | Tipo do sistema de arquivos |
| `PARTUUID` | Identificador da partição na tabela de partições |

---

#### 5. Como criar um ponto de montagem

Crie uma pasta para servir como ponto de montagem:

```bash
sudo mkdir -p /mnt/hdexterno
```

Monte a partição:

```bash
sudo mount /dev/sdb1 /mnt/hdexterno
```

Acesse os arquivos:

```bash
cd /mnt/hdexterno
ls -la
```

---

#### 6. Como desmontar uma partição

Desmontar pelo ponto de montagem:

```bash
sudo umount /mnt/hdexterno
```

Ou pelo dispositivo:

```bash
sudo umount /dev/sdb1
```

Se aparecer erro de alvo ocupado:

```bash
umount: /mnt/hdexterno: target is busy
```

Verifique quem está usando o diretório:

```bash
sudo lsof +f -- /mnt/hdexterno
```

ou:

```bash
sudo fuser -vm /mnt/hdexterno
```

Depois, feche arquivos, terminais ou programas que estejam usando o disco.

---

#### 7. Montagem por tipo de sistema de arquivos

| Sistema de arquivos | Comando |
|---|---|
| `ext4` | `sudo mount -t ext4 /dev/sdb1 /mnt/dados` |
| `ntfs` | `sudo mount -t ntfs3 /dev/sdb1 /mnt/windows` |
| `exfat` | `sudo mount -t exfat /dev/sdb1 /mnt/hdexterno` |
| `vfat` | `sudo mount -t vfat /dev/sdb1 /mnt/pendrive` |

---

#### 8. Permissões em pontos de montagem

#### Sistemas Linux, como `ext4`

```bash
sudo chown -R $USER:$USER /mnt/hdexterno
```

Ou para um usuário específico:

```bash
sudo chown -R douglas:douglas /mnt/hdexterno
```

---

#### Sistemas `ntfs`, `exfat` ou `vfat`

Esses sistemas não usam permissões Linux da mesma forma que `ext4`. Normalmente, as permissões são definidas no momento da montagem.

Exemplo com `ntfs`:

```bash
sudo mount -t ntfs3 -o uid=$(id -u),gid=$(id -g),umask=022 /dev/sdb1 /mnt/hdexterno
```

Permissão mais aberta:

```bash
sudo mount -t ntfs3 -o uid=$(id -u),gid=$(id -g),umask=000 /dev/sdb1 /mnt/hdexterno
```

---

#### 9. Montagem automática com `/etc/fstab`

O arquivo `/etc/fstab` define quais partições serão montadas automaticamente durante a inicialização do sistema.

Antes de editar, faça backup:

```bash
sudo cp /etc/fstab /etc/fstab.bkp
```

Editar o arquivo:

```bash
sudo nano /etc/fstab
```

---

#### Exemplo para `ext4`

```bash
UUID=xxxx-xxxx /mnt/dados ext4 defaults 0 2
```

#### Exemplo para `ntfs`

```bash
UUID=xxxx-xxxx /mnt/windows ntfs3 defaults,uid=1000,gid=1000,umask=022 0 0
```

#### Exemplo para `exfat`

```bash
UUID=xxxx-xxxx /mnt/hdexterno exfat defaults,uid=1000,gid=1000,umask=022,nofail 0 0
```

#### Exemplo para EFI

```bash
UUID=xxxx-xxxx /boot/efi vfat umask=0077 0 1
```

---

#### 10. Testar o `/etc/fstab`

Após editar o `/etc/fstab`, teste sem reiniciar:

```bash
sudo mount -a
```

Se não aparecer erro, a configuração está válida.

Verifique a montagem:

```bash
lsblk
df -h
findmnt
```

---

#### 11. Opções comuns no `/etc/fstab`

| Opção | Função |
|---|---|
| `defaults` | Usa opções padrão de montagem |
| `auto` | Monta automaticamente |
| `noauto` | Não monta automaticamente no boot |
| `rw` | Monta com leitura e escrita |
| `ro` | Monta somente leitura |
| `user` | Permite que usuário comum monte |
| `users` | Permite que qualquer usuário monte/desmonte |
| `uid=1000` | Define o dono dos arquivos montados |
| `gid=1000` | Define o grupo dos arquivos montados |
| `umask=022` | Define permissões padrão mais restritas |
| `umask=000` | Define permissões abertas para todos |
| `nofail` | Não impede o boot se o disco estiver ausente |

---

#### 12. Exemplo prático de montagem manual

#### 1. Listar discos

```bash
lsblk
```

#### 2. Verificar UUID e tipo

```bash
sudo blkid /dev/sdb1
```

#### 3. Criar ponto de montagem

```bash
sudo mkdir -p /mnt/hdexterno
```

#### 4. Montar partição

```bash
sudo mount -t exfat /dev/sdb1 /mnt/hdexterno
```

#### 5. Acessar arquivos

```bash
cd /mnt/hdexterno
ls -la
```

#### 6. Desmontar

```bash
sudo umount /mnt/hdexterno
```

---

#### 13. Exemplo prático de montagem automática

#### 1. Criar ponto de montagem

```bash
sudo mkdir -p /mnt/hdexterno
```

#### 2. Descobrir UUID

```bash
sudo blkid /dev/sdb1
```

#### 3. Editar `/etc/fstab`

```bash
sudo nano /etc/fstab
```

Adicionar linha:

```bash
UUID=A1B2-C3D4 /mnt/hdexterno exfat defaults,uid=1000,gid=1000,umask=022,nofail 0 0
```

#### 4. Testar

```bash
sudo mount -a
```

#### 5. Verificar

```bash
df -h
lsblk
```

---

#### 14. Comandos mais usados

| Comando | Função |
|---|---|
| `lsblk` | Lista discos, partições e pontos de montagem |
| `df -h` | Mostra espaço usado e disponível |
| `sudo blkid` | Mostra UUID e tipo das partições |
| `findmnt` | Mostra árvore de montagens |
| `mount` | Mostra ou realiza montagens |
| `sudo mount /dev/sdb1 /mnt/hdexterno` | Monta uma partição |
| `sudo umount /mnt/hdexterno` | Desmonta uma partição |
| `sudo mkdir -p /mnt/hdexterno` | Cria ponto de montagem |
| `sudo nano /etc/fstab` | Edita montagens automáticas |
| `sudo mount -a` | Testa e aplica o `/etc/fstab` |

---

#### 15. Observações importantes

- Faça backup do `/etc/fstab` antes de editar.
- Prefira usar `UUID` no `/etc/fstab`, pois nomes como `/dev/sdb1` podem mudar.
- Use `/mnt` para montagens manuais.
- Use `/media` para dispositivos montados automaticamente pela interface gráfica.
- Para `ntfs`, `exfat` e `vfat`, configure `uid`, `gid` e `umask` quando precisar controlar permissões.
- Use `nofail` em discos externos para evitar problemas de inicialização caso o disco não esteja conectado.

# Gerenciamento de pacotes no Linux

Gerenciar pacotes no Linux significa **instalar, remover, atualizar, pesquisar e manter programas** no sistema operacional.

Cada família de distribuição Linux utiliza um gerenciador de pacotes diferente.

---

## 1. Debian, Ubuntu, Linux Mint, Pop!_OS e Zorin OS

Essas distribuições usam pacotes no formato `.deb` e o gerenciador principal é o **APT**.

### Atualizar a lista de pacotes

```bash
sudo apt update
```

Atualiza a lista de pacotes disponíveis nos repositórios configurados no sistema.

### Atualizar os pacotes instalados

```bash
sudo apt upgrade -y
```

Atualiza os pacotes já instalados.

### Instalar um pacote

```bash
sudo apt install nome_do_pacote
```

Exemplo:

```bash
sudo apt install git
```

### Remover um pacote

```bash
sudo apt remove nome_do_pacote
```

Exemplo:

```bash
sudo apt remove git
```

### Remover pacote e arquivos de configuração

```bash
sudo apt purge nome_do_pacote
```

Exemplo:

```bash
sudo apt purge nginx
```

### Pesquisar um pacote

```bash
apt search nome_do_pacote
```

Exemplo:

```bash
apt search docker
```

### Ver informações de um pacote

```bash
apt show nome_do_pacote
```

Exemplo:

```bash
apt show nginx
```

### Remover pacotes desnecessários

```bash
sudo apt autoremove
```

### Limpar cache de pacotes

```bash
sudo apt clean
```

---

## 2. Instalação manual de pacotes `.deb` com DPKG

O `dpkg` é usado para instalar pacotes locais no formato `.deb`.

### Instalar pacote `.deb`

```bash
sudo dpkg -i pacote.deb
```

Exemplo:

```bash
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

### Corrigir dependências quebradas

```bash
sudo apt install -f
```

Esse comando é útil quando o `dpkg` instala um pacote, mas faltam dependências.

### Remover pacote instalado via `dpkg`

```bash
sudo dpkg -r nome_do_pacote
```

Exemplo:

```bash
sudo dpkg -r google-chrome-stable
```

### Listar pacotes instalados

```bash
dpkg -l
```

Filtrar por nome:

```bash
dpkg -l | grep nginx
```

---

## 3. Fedora, Rocky Linux, AlmaLinux e RHEL

Essas distribuições usam pacotes no formato `.rpm` e o gerenciador principal é o **DNF**.

### Atualizar pacotes

```bash
sudo dnf update -y
```

### Instalar pacote

```bash
sudo dnf install nome_do_pacote
```

Exemplo:

```bash
sudo dnf install git
```

### Remover pacote

```bash
sudo dnf remove nome_do_pacote
```

Exemplo:

```bash
sudo dnf remove git
```

### Pesquisar pacote

```bash
dnf search nome_do_pacote
```

Exemplo:

```bash
dnf search docker
```

### Ver informações de um pacote

```bash
dnf info nome_do_pacote
```

Exemplo:

```bash
dnf info nginx
```

### Limpar cache

```bash
sudo dnf clean all
```

---

## 4. Instalação manual de pacotes `.rpm`

O `rpm` é usado para instalar pacotes locais no formato `.rpm`.

### Instalar pacote `.rpm`

```bash
sudo rpm -i pacote.rpm
```

### Atualizar ou instalar pacote `.rpm`

```bash
sudo rpm -Uvh pacote.rpm
```

### Remover pacote

```bash
sudo rpm -e nome_do_pacote
```

### Listar pacotes instalados

```bash
rpm -qa
```

Filtrar por nome:

```bash
rpm -qa | grep nginx
```

---

## 5. Arch Linux, Manjaro e EndeavourOS

Essas distribuições usam o gerenciador **Pacman**.

### Atualizar o sistema

```bash
sudo pacman -Syu
```

### Instalar pacote

```bash
sudo pacman -S nome_do_pacote
```

Exemplo:

```bash
sudo pacman -S git
```

### Remover pacote

```bash
sudo pacman -R nome_do_pacote
```

Exemplo:

```bash
sudo pacman -R git
```

### Remover pacote e dependências não utilizadas

```bash
sudo pacman -Rns nome_do_pacote
```

### Pesquisar pacote

```bash
pacman -Ss nome_do_pacote
```

Exemplo:

```bash
pacman -Ss docker
```

### Ver pacotes instalados

```bash
pacman -Q
```

---

## 6. openSUSE e SUSE Linux Enterprise

Essas distribuições usam o gerenciador **Zypper**.

### Atualizar repositórios

```bash
sudo zypper refresh
```

### Atualizar sistema

```bash
sudo zypper update
```

### Instalar pacote

```bash
sudo zypper install nome_do_pacote
```

Exemplo:

```bash
sudo zypper install git
```

### Remover pacote

```bash
sudo zypper remove nome_do_pacote
```

### Pesquisar pacote

```bash
zypper search nome_do_pacote
```

### Ver informações de um pacote

```bash
zypper info nome_do_pacote
```

---

## 7. Alpine Linux

O Alpine Linux usa o gerenciador **APK**.

### Atualizar lista de pacotes

```bash
sudo apk update
```

### Atualizar pacotes instalados

```bash
sudo apk upgrade
```

### Instalar pacote

```bash
sudo apk add nome_do_pacote
```

Exemplo:

```bash
sudo apk add git
```

### Remover pacote

```bash
sudo apk del nome_do_pacote
```

### Pesquisar pacote

```bash
apk search nome_do_pacote
```

### Ver informações de um pacote

```bash
apk info nome_do_pacote
```

---

## 8. Tabela resumo dos gerenciadores

| Distribuição/Família | Formato | Gerenciador principal | Comando de instalação |
|---|---|---|---|
| Debian, Ubuntu, Mint, Pop!_OS, Zorin OS | `.deb` | `apt` | `sudo apt install pacote` |
| Debian, Ubuntu, Mint, Pop!_OS, Zorin OS | `.deb` | `dpkg` | `sudo dpkg -i pacote.deb` |
| Fedora, RHEL, Rocky Linux, AlmaLinux | `.rpm` | `dnf` | `sudo dnf install pacote` |
| Fedora, RHEL, Rocky Linux, AlmaLinux | `.rpm` | `rpm` | `sudo rpm -i pacote.rpm` |
| Arch Linux, Manjaro, EndeavourOS | Pacman package | `pacman` | `sudo pacman -S pacote` |
| openSUSE, SUSE Linux Enterprise | `.rpm` | `zypper` | `sudo zypper install pacote` |
| Alpine Linux | `.apk` | `apk` | `sudo apk add pacote` |

---

## 9. Tabela de comandos por ação

| Ação | Debian/Ubuntu | Fedora/RHEL | Arch/Manjaro | openSUSE | Alpine |
|---|---|---|---|---|---|
| Atualizar lista | `sudo apt update` | `sudo dnf check-update` | `sudo pacman -Sy` | `sudo zypper refresh` | `sudo apk update` |
| Atualizar sistema | `sudo apt upgrade -y` | `sudo dnf update -y` | `sudo pacman -Syu` | `sudo zypper update` | `sudo apk upgrade` |
| Instalar pacote | `sudo apt install pacote` | `sudo dnf install pacote` | `sudo pacman -S pacote` | `sudo zypper install pacote` | `sudo apk add pacote` |
| Remover pacote | `sudo apt remove pacote` | `sudo dnf remove pacote` | `sudo pacman -R pacote` | `sudo zypper remove pacote` | `sudo apk del pacote` |
| Pesquisar pacote | `apt search pacote` | `dnf search pacote` | `pacman -Ss pacote` | `zypper search pacote` | `apk search pacote` |
| Ver informações | `apt show pacote` | `dnf info pacote` | `pacman -Si pacote` | `zypper info pacote` | `apk info pacote` |
| Listar instalados | `dpkg -l` | `rpm -qa` | `pacman -Q` | `zypper search -i` | `apk info` |
| Limpar cache | `sudo apt clean` | `sudo dnf clean all` | `sudo pacman -Sc` | `sudo zypper clean` | `sudo apk cache clean` |

---

## 10. Comandos mais usados no Ubuntu/Debian

```bash
sudo apt update
sudo apt upgrade -y
sudo apt install nome_do_pacote
sudo apt remove nome_do_pacote
sudo apt purge nome_do_pacote
sudo apt autoremove
apt search nome_do_pacote
apt show nome_do_pacote
```

---

## 11. Exemplo prático no Ubuntu

### Instalar o Git

```bash
sudo apt update
sudo apt install git -y
```

### Verificar instalação

```bash
git --version
```

### Remover o Git

```bash
sudo apt remove git
```

---

## 12. Diferença entre `apt`, `dpkg`, `dnf`, `rpm`, `pacman`, `zypper` e `apk`

| Ferramenta | Tipo | Uso principal |
|---|---|---|
| `apt` | Alto nível | Instala, remove e atualiza pacotes em Debian/Ubuntu com resolução automática de dependências |
| `dpkg` | Baixo nível | Instala e remove pacotes locais `.deb` |
| `dnf` | Alto nível | Gerencia pacotes em Fedora, RHEL, Rocky Linux e AlmaLinux |
| `rpm` | Baixo nível | Instala e remove pacotes locais `.rpm` |
| `pacman` | Alto nível | Gerencia pacotes em Arch Linux e derivados |
| `zypper` | Alto nível | Gerencia pacotes em openSUSE e SUSE |
| `apk` | Alto nível | Gerencia pacotes em Alpine Linux |

---

## 13. Boas práticas

- Use sempre o gerenciador principal da sua distribuição.
- No Ubuntu/Debian, execute `sudo apt update` antes de instalar novos pacotes.
- Use `apt`, `dnf`, `pacman`, `zypper` ou `apk` sempre que possível, pois eles resolvem dependências automaticamente.
- Use `dpkg` e `rpm` apenas para instalar arquivos locais, como `.deb` ou `.rpm`.
- Use `purge` no Ubuntu/Debian quando quiser remover também arquivos de configuração.
- Use `autoremove` no Ubuntu/Debian para limpar dependências não utilizadas.
- Evite instalar pacotes de fontes desconhecidas.
- Antes de remover pacotes importantes, verifique o que será removido.

# Gerenciamento de processos no Linux

Gerenciar processos no Linux significa **visualizar, monitorar, encerrar, priorizar e controlar programas em execução** no sistema.

Um **processo** é qualquer programa ou comando em execução, como navegador, terminal, serviço, script, banco de dados ou aplicação.

---

## 1. Ver processos em execução

### Listar todos os processos

```bash
ps aux
```

Exemplo de saída:

```bash
USER       PID  %CPU %MEM COMMAND
root         1   0.0  0.1 /sbin/init
douglas   2450   2.5  1.8 firefox
douglas   3102   0.1  0.3 bash
```

| Coluna | Significado |
|---|---|
| `USER` | Usuário que iniciou o processo |
| `PID` | Identificador do processo |
| `%CPU` | Uso de CPU |
| `%MEM` | Uso de memória |
| `COMMAND` | Comando ou programa executado |

---

## 2. Filtrar processos com `grep`

### Procurar processo pelo nome

```bash
ps aux | grep nginx
```

Exemplo:

```bash
ps aux | grep python
```

### Evitar que o próprio `grep` apareça no resultado

```bash
ps aux | grep "[p]ython"
```

---

## 3. Monitorar processos em tempo real

### Usando `top`

```bash
top
```

Comandos úteis dentro do `top`:

| Tecla | Função |
|---|---|
| `q` | Sair |
| `k` | Encerrar processo |
| `P` | Ordenar por uso de CPU |
| `M` | Ordenar por uso de memória |

### Usando `htop`

```bash
htop
```

Instalar no Ubuntu/Debian:

```bash
sudo apt install htop
```

No `htop`, é possível navegar com as setas, selecionar processos e encerrar usando `F9`.

---

## 4. Identificar o PID de um processo

O **PID** é o identificador numérico de um processo.

### Usando `pidof`

```bash
pidof nome_do_processo
```

Exemplo:

```bash
pidof nginx
```

### Usando `pgrep`

```bash
pgrep nome_do_processo
```

Exemplo:

```bash
pgrep python
```

Mostrar também o comando:

```bash
pgrep -a python
```

---

## 5. Encerrar processos

### Encerrar processo pelo PID

```bash
kill PID
```

Exemplo:

```bash
kill 2450
```

Esse comando envia o sinal padrão `SIGTERM`, solicitando o encerramento normal do processo.

### Forçar encerramento

```bash
kill -9 PID
```

Exemplo:

```bash
kill -9 2450
```

O sinal `-9` força o encerramento imediato e deve ser usado apenas quando o processo não responde.

### Encerrar processo pelo nome

```bash
pkill nome_do_processo
```

Exemplo:

```bash
pkill firefox
```

### Encerrar todos os processos com determinado nome

```bash
killall nome_do_processo
```

Exemplo:

```bash
killall python
```

---

## 6. Sinais mais comuns

| Sinal | Nome | Função |
|---|---|---|
| `1` | `SIGHUP` | Recarrega ou reinicia configuração em alguns processos |
| `2` | `SIGINT` | Interrompe o processo, semelhante ao `Ctrl + C` |
| `9` | `SIGKILL` | Força o encerramento imediato |
| `15` | `SIGTERM` | Solicita encerramento normal |
| `18` | `SIGCONT` | Continua processo pausado |
| `19` | `SIGSTOP` | Pausa processo |

Encerrar normalmente:

```bash
kill -15 2450
```

Forçar encerramento:

```bash
kill -9 2450
```

---

## 7. Pausar e continuar processos

### Pausar processo

```bash
kill -STOP PID
```

Exemplo:

```bash
kill -STOP 2450
```

### Continuar processo pausado

```bash
kill -CONT PID
```

Exemplo:

```bash
kill -CONT 2450
```

---

## 8. Primeiro plano e segundo plano

### Executar comando normalmente

```bash
python script.py
```

O terminal fica ocupado até o processo terminar.

### Executar em segundo plano

```bash
python script.py &
```

O `&` executa o comando em segundo plano e libera o terminal.

### Ver processos em segundo plano do terminal atual

```bash
jobs
```

### Trazer processo para primeiro plano

```bash
fg
```

Se houver mais de um processo:

```bash
fg %1
```

### Enviar processo para segundo plano

Durante a execução de um comando, pressione:

```bash
Ctrl + Z
```

Isso pausa o processo. Depois execute:

```bash
bg
```

---

## 9. Manter processo rodando após fechar o terminal

### Usando `nohup`

```bash
nohup comando &
```

Exemplo:

```bash
nohup python script.py &
```

A saída normalmente é gravada em:

```bash
nohup.out
```

### Salvar saída em arquivo específico

```bash
nohup python script.py > saida.log 2>&1 &
```

---

## 10. Ver consumo de recursos

### Ver uso de CPU e memória

```bash
top
```

ou:

```bash
htop
```

### Ver memória RAM

```bash
free -h
```

### Ver uso de disco

```bash
df -h
```

### Ver tamanho de diretórios

```bash
du -sh *
```

---

## 11. Ver árvore de processos

```bash
pstree
```

Instalar no Ubuntu/Debian:

```bash
sudo apt install psmisc
```

Mostrar PIDs:

```bash
pstree -p
```

---

## 12. Ver processos de um usuário específico

```bash
ps -u nome_usuario
```

Exemplo:

```bash
ps -u douglas
```

Com mais detalhes:

```bash
ps aux | grep douglas
```

---

## 13. Ver processos usando uma porta

### Usando `ss`

```bash
sudo ss -tulnp
```

Filtrar por porta:

```bash
sudo ss -tulnp | grep 80
```

### Usando `lsof`

```bash
sudo lsof -i :80
```

Exemplo:

```bash
sudo lsof -i :443
```

---

## 14. Encerrar processo que usa uma porta

### Descobrir o processo

```bash
sudo lsof -i :8000
```

Exemplo de saída:

```bash
COMMAND  PID USER
python  2450 douglas
```

### Encerrar normalmente

```bash
kill 2450
```

### Forçar encerramento

```bash
kill -9 2450
```

---

## 15. Alterar prioridade de processos

No Linux, a prioridade é controlada pelo valor **nice**.

Quanto menor o valor, maior a prioridade.

| Nice | Prioridade |
|---|---|
| `-20` | Prioridade máxima |
| `0` | Prioridade padrão |
| `19` | Prioridade baixa |

### Iniciar processo com prioridade menor

```bash
nice -n 10 comando
```

Exemplo:

```bash
nice -n 10 python script.py
```

### Alterar prioridade de processo em execução

```bash
renice 10 -p PID
```

Exemplo:

```bash
renice 10 -p 2450
```

Para aumentar prioridade, geralmente é necessário usar `sudo`:

```bash
sudo renice -5 -p 2450
```

---

## 16. Gerenciar serviços com `systemctl`

Muitos processos são serviços do sistema, como `nginx`, `docker`, `postgresql`, `ssh` e outros.

### Ver status de um serviço

```bash
sudo systemctl status nome_servico
```

Exemplo:

```bash
sudo systemctl status nginx
```

### Iniciar serviço

```bash
sudo systemctl start nome_servico
```

### Parar serviço

```bash
sudo systemctl stop nome_servico
```

### Reiniciar serviço

```bash
sudo systemctl restart nome_servico
```

### Recarregar configuração sem reiniciar totalmente

```bash
sudo systemctl reload nome_servico
```

Exemplo:

```bash
sudo systemctl reload nginx
```

### Habilitar serviço no boot

```bash
sudo systemctl enable nome_servico
```

### Desabilitar serviço no boot

```bash
sudo systemctl disable nome_servico
```

---

## 17. Ver logs de processos e serviços

### Ver logs de um serviço

```bash
journalctl -u nome_servico
```

Exemplo:

```bash
journalctl -u nginx
```

### Ver logs em tempo real

```bash
journalctl -u nome_servico -f
```

Exemplo:

```bash
journalctl -u docker -f
```

### Ver logs desde hoje

```bash
journalctl -u nome_servico --since "today"
```

Exemplo:

```bash
journalctl -u nginx --since "today"
```

### Filtrar erros nos logs

```bash
journalctl -u nginx --since "today" | grep -Ei "error|failed|timeout|refused"
```

---

## 18. Comandos mais usados

| Comando | Função |
|---|---|
| `ps aux` | Lista todos os processos |
| `ps aux | grep nome` | Filtra processo pelo nome |
| `top` | Monitora processos em tempo real |
| `htop` | Monitora processos com interface melhor |
| `pidof nome` | Mostra PID de um processo |
| `pgrep nome` | Procura PID pelo nome |
| `pgrep -a nome` | Mostra PID e comando |
| `kill PID` | Encerra processo normalmente |
| `kill -9 PID` | Força encerramento |
| `pkill nome` | Encerra processo pelo nome |
| `killall nome` | Encerra todos os processos com o nome informado |
| `jobs` | Mostra processos em segundo plano no terminal atual |
| `fg` | Traz processo para primeiro plano |
| `bg` | Continua processo em segundo plano |
| `nohup comando &` | Mantém processo rodando após fechar terminal |
| `pstree -p` | Mostra árvore de processos com PID |
| `sudo ss -tulnp` | Mostra portas e processos |
| `sudo lsof -i :porta` | Mostra processo usando uma porta |
| `nice -n valor comando` | Inicia processo com prioridade definida |
| `renice valor -p PID` | Altera prioridade de processo existente |
| `systemctl status serviço` | Verifica status de serviço |
| `journalctl -u serviço -f` | Acompanha logs do serviço |

---

## 19. Exemplos práticos

### Encontrar e encerrar um processo Python

```bash
ps aux | grep python
```

Depois:

```bash
kill PID
```

Se necessário:

```bash
kill -9 PID
```

### Descobrir quem está usando a porta 8000

```bash
sudo lsof -i :8000
```

Depois:

```bash
kill PID
```

### Ver processos consumindo mais CPU

```bash
top
```

Dentro do `top`, pressione:

```bash
P
```

### Ver processos consumindo mais memória

```bash
top
```

Dentro do `top`, pressione:

```bash
M
```

### Rodar script em segundo plano e salvar log

```bash
nohup python script.py > script.log 2>&1 &
```

### Ver logs de um serviço em tempo real

```bash
journalctl -u nginx -f
```

---

## 20. Resumo rápido

```bash
ps aux
top
htop
pgrep nome
kill PID
kill -9 PID
pkill nome
jobs
fg
bg
nohup comando &
sudo lsof -i :porta
sudo systemctl status serviço
journalctl -u serviço -f
```

Esses comandos permitem visualizar processos, identificar consumo de recursos, encerrar programas travados, controlar execução em segundo plano, verificar portas em uso e acompanhar logs de serviços.

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