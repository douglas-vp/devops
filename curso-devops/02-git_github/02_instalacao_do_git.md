# 2. Instalação do Git

Antes de usar o Git, é necessário instalar a ferramenta no sistema operacional.

A instalação varia conforme a distribuição Linux ou o sistema utilizado.

---

## 2.1 Verificar se o Git já está instalado

```bash
git --version
```

Exemplo de saída:

```bash
git version 2.43.0
```

Se o comando retornar uma versão, o Git já está instalado.

---

## 2.2 Instalar Git no Ubuntu, Debian, Linux Mint, Pop!_OS e Zorin OS

Atualizar a lista de pacotes:

```bash
sudo apt update
```

Instalar o Git:

```bash
sudo apt install git -y
```

Verificar instalação:

```bash
git --version
```

---

## 2.3 Instalar Git no Fedora, Rocky Linux, AlmaLinux e RHEL

```bash
sudo dnf install git -y
```

Verificar instalação:

```bash
git --version
```

---

## 2.4 Instalar Git no Arch Linux e Manjaro

```bash
sudo pacman -S git
```

Verificar instalação:

```bash
git --version
```

---

## 2.5 Instalar Git no openSUSE

```bash
sudo zypper install git
```

Verificar instalação:

```bash
git --version
```

---

## 2.6 Instalar Git no Alpine Linux

```bash
sudo apk add git
```

Verificar instalação:

```bash
git --version
```

---

## 2.7 Instalar Git no Windows

No Windows, o Git normalmente é instalado por meio do instalador oficial do Git for Windows.

Após a instalação, é possível usar:

- Git Bash;
- PowerShell;
- Prompt de Comando;
- terminal integrado do VS Code;
- terminal do PyCharm.

Verificar instalação:

```bash
git --version
```

---

## 2.8 Instalar Git no macOS

Com Homebrew:

```bash
brew install git
```

Verificar instalação:

```bash
git --version
```

Também é possível instalar o Git ao instalar as ferramentas de linha de comando do Xcode.

---

## 2.9 Tabela resumo

| Sistema | Comando de instalação |
|---|---|
| Ubuntu/Debian | `sudo apt install git -y` |
| Fedora/RHEL | `sudo dnf install git -y` |
| Arch/Manjaro | `sudo pacman -S git` |
| openSUSE | `sudo zypper install git` |
| Alpine | `sudo apk add git` |
| macOS com Homebrew | `brew install git` |
| Windows | Instalar Git for Windows |
