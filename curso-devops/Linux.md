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