# Sistema de Arquivos no Linux

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
