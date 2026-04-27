# Distribuições Linux e Gerenciadores de Pacotes

## Objetivo

Compreender as principais famílias de distribuições Linux, os formatos de pacotes e os gerenciadores utilizados em cada ecossistema.

---

## 1. Distribuições baseadas em Debian/Ubuntu

Exemplos:

- Debian
- Ubuntu
- Linux Mint
- Pop!_OS
- Elementary OS
- Zorin OS

Essas distribuições utilizam pacotes no formato **`.deb`**.

| Gerenciador | Tipo | Uso principal |
|---|---|---|
| `apt` | Alto nível | Instala, remove, atualiza e pesquisa pacotes em repositórios. |
| `dpkg` | Baixo nível | Instala, remove e consulta pacotes locais `.deb`. |

---

## 2. Distribuições baseadas em Red Hat/Fedora

Exemplos:

- Fedora
- Red Hat Enterprise Linux
- Rocky Linux
- AlmaLinux
- CentOS Stream

Essas distribuições utilizam pacotes no formato **`.rpm`**.

| Gerenciador | Tipo | Uso principal |
|---|---|---|
| `dnf` | Alto nível | Gerencia pacotes e dependências em distribuições modernas da família Red Hat. |
| `rpm` | Baixo nível | Instala, remove e consulta pacotes locais `.rpm`. |

---

## 3. Distribuições baseadas em Arch Linux

Exemplos:

- Arch Linux
- Manjaro
- EndeavourOS
- Garuda Linux

Essas distribuições usam o gerenciador **`pacman`**.

| Gerenciador | Tipo | Uso principal |
|---|---|---|
| `pacman` | Alto nível | Atualiza o sistema, instala, remove e pesquisa pacotes no ecossistema Arch. |

---

## 4. Distribuições baseadas em openSUSE/SUSE

Exemplos:

- openSUSE Leap
- openSUSE Tumbleweed
- SUSE Linux Enterprise

Essas distribuições utilizam o gerenciador **`zypper`**.

| Gerenciador | Tipo | Uso principal |
|---|---|---|
| `zypper` | Alto nível | Atualiza repositórios, instala, remove, pesquisa e atualiza pacotes. |

---

## 5. Alpine Linux

Exemplos:

- Alpine Linux
- Containers baseados em Alpine

O Alpine Linux utiliza o gerenciador **`apk`**.

| Gerenciador | Tipo | Uso principal |
|---|---|---|
| `apk` | Alto nível | Instala, remove, atualiza e pesquisa pacotes em Alpine Linux. |

---

## 6. Tabela resumo

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

## 7. Síntese do aprendizado

- Distribuições da mesma família normalmente compartilham formato de pacote e gerenciadores semelhantes.
- Ferramentas de alto nível, como `apt`, `dnf`, `pacman`, `zypper` e `apk`, são recomendadas para uso diário.
- Ferramentas de baixo nível, como `dpkg` e `rpm`, são mais adequadas para pacotes locais.
- Os comandos detalhados de instalação, remoção, atualização e pesquisa ficam no arquivo `07_gerenciamento_de_pacotes.md`.
