# 3. Configuração inicial e primeiro repositório

Após instalar o Git, é necessário configurar informações básicas do usuário e criar o primeiro repositório.

Essas configurações são usadas nos commits e ajudam a identificar o autor das alterações.

---

## 3.1 Configurar o nome do usuário

```bash
git config --global user.name "Douglas Pontes"
```

Essa configuração define o nome associado aos commits criados pelo usuário.

Verificar:

```bash
git config --global user.name
```

---

## 3.2 Configurar o e-mail do usuário

```bash
git config --global user.email "douglas@email.com"
```

O e-mail deve ser o mesmo usado na plataforma remota, como GitHub, quando houver integração com repositórios online.

Verificar:

```bash
git config --global user.email
```

---

## 3.3 Configurar o editor padrão global

O editor padrão é usado pelo Git quando ele precisa abrir uma mensagem de commit, merge ou rebase.

Exemplo com Nano:

```bash
git config --global core.editor "nano"
```

Exemplo com Vim:

```bash
git config --global core.editor "vim"
```

Exemplo com VS Code:

```bash
git config --global core.editor "code --wait"
```

---

## 3.4 Configurar a branch inicial padrão

```bash
git config --global init.defaultBranch main
```

Essa configuração faz com que novos repositórios iniciem com a branch `main`.

---

## 3.5 Configurar editor no nível do sistema

```bash
sudo git config --system core.editor "nano"
```

Essa configuração vale para todos os usuários da máquina e normalmente requer permissão administrativa.

---

## 3.6 Listar configurações do Git

```bash
git config --list
```

Exemplo de saída:

```bash
user.name=Douglas Pontes
user.email=douglas@email.com
core.editor=nano
init.defaultbranch=main
```

---

## 3.7 Herança de configuração

O Git trabalha com níveis de configuração.

| Nível | Comando | Abrangência |
|---|---|---|
| Sistema | `--system` | Todos os usuários da máquina |
| Global | `--global` | Usuário atual |
| Local | sem flag ou `--local` | Repositório atual |

Ordem de prioridade:

```bash
local > global > system
```

Isso significa que uma configuração local sobrescreve uma configuração global, e uma configuração global sobrescreve uma configuração do sistema.

---

## 3.8 Ver origem das configurações

```bash
git config --list --show-origin
```

Esse comando mostra de qual arquivo cada configuração foi carregada.

---

## 3.9 Criar o primeiro repositório com `git init`

Criar uma pasta:

```bash
mkdir projeto-git
cd projeto-git
```

Inicializar o repositório:

```bash
git init
```

Exemplo de saída:

```bash
Initialized empty Git repository in /home/douglas/projeto-git/.git/
```

---

## 3.10 Criar o primeiro commit

```bash
echo "# Projeto Git" > README.md
git status
git add README.md
git commit -m "Adiciona README inicial"
```

---

## 3.11 Fluxo completo

```bash
git config --global user.name "Douglas Pontes"
git config --global user.email "douglas@email.com"
git config --global core.editor "nano"
git config --global init.defaultBranch main
mkdir projeto-git
cd projeto-git
git init
echo "# Projeto Git" > README.md
git status
git add README.md
git commit -m "Adiciona README inicial"
```

---

## 3.12 Tabela resumo

| Comando | Função |
|---|---|
| `git config --global user.name "Nome"` | Define o nome do autor dos commits |
| `git config --global user.email "email"` | Define o e-mail do autor dos commits |
| `git config --global core.editor "nano"` | Define o editor padrão global |
| `git config --global init.defaultBranch main` | Define a branch inicial padrão |
| `git config --system core.editor "nano"` | Define editor padrão para todos os usuários |
| `git config --list` | Lista configurações ativas |
| `git config --list --show-origin` | Mostra configurações e arquivos de origem |
| `git init` | Inicializa um repositório Git |
