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
