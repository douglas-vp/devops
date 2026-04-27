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
