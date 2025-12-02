# Git Básico com GitHub

Este lab apresenta comandos e conceitos básicos do Git com foco em uso prático no GitHub. 
Ao longo do material são abordados:

- Instalação
- Clonagem de repositório
- Adição de arquivos
- Criação de commits
- Envio para o GitHub (push)
- Criação de branch
- Realização de merge
- Criação de Pull Request

---

## 1. Instalação do Git

### Windows
- Download em: https://git-scm.com/download/win  
- Instalação recomendada com as opções padrão.

### Linux (Debian/Ubuntu)
```bash
sudo apt update
sudo apt install git -y
```

### macOS (usando Homebrew)
```bash
brew install git
```

Verificação da instalação:
```bash
git --version
```

Configuração global de nome e e-mail:
```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```

---

## 2. Clonar um repositório

Após criar um repositório no GitHub com um README, a clonagem pode ser feita com:

```bash
git clone https://github.com/seu-usuario/nome-do-repo.git
cd nome-do-repo
```

---

## 3. Adicionar arquivos

Criação de um arquivo de exemplo:
```bash
echo "# Meu projeto" > projeto.md
```

Adição do arquivo ao controle de versão:
```bash
git add projeto.md
```

---

## 4. Fazer commit

Criação de um commit com mensagem descritiva:
```bash
git commit -m "Adiciona projeto.md inicial"
```

---

## 5. Enviar para o GitHub (push)

Envio das alterações para o repositório remoto:
```bash
git push origin main
```

> Utilizar `main` ou `master` conforme o nome da branch principal configurada no repositório.

---

## 6. Criar branch

Criação de uma nova branch e troca para ela:
```bash
git checkout -b nova-feature
```

Alteração do arquivo, adição e commit:
```bash
echo "Adicionando nova funcionalidade" >> projeto.md
git add projeto.md
git commit -m "Nova feature adicionada"
```

---

## 7. Fazer push da nova branch

Envio da nova branch para o repositório remoto:
```bash
git push origin nova-feature
```

---

## 8. Criar Pull Request no GitHub

No GitHub, os passos gerais são:

- Acessar o repositório.
- Clicar em **"Compare & pull request"**.
- Adicionar um título e uma descrição adequados.
- Clicar em **"Create pull request"**.

---

## 9. Fazer merge no GitHub

Para concluir a integração da branch:

- Acessar a aba **"Pull requests"**.
- Selecionar a Pull Request criada.
- Clicar em **"Merge pull request"**.
- Confirmar em **"Confirm merge"**.

---

## 10. Atualizar a branch local

Retornar para a branch principal:
```bash
git checkout main
```

Atualizar o conteúdo com o estado mais recente do remoto:
```bash
git pull origin main
```

---

# Parte Intermediária do Git

A partir dos comandos básicos, são apresentados recursos mais comuns em projetos reais.

## 11. Tag (versões)

Criação de uma tag anotando uma versão:
```bash
git tag v1.0.0
```

Envio da tag para o repositório remoto:
```bash
git push origin v1.0.0
```

---

## 12. Ignorar arquivos (usando .gitignore)

Criação de um arquivo `.gitignore` com padrões de exclusão:
```txt
node_modules
*.log
.env
```

Adição e commit do `.gitignore`:
```bash
git add .gitignore
git commit -m "Adiciona .gitignore"
```

---

## 13. Ver arquivos modificados entre commits

Comparação de alterações entre dois commits específicos:
```bash
git diff <commit-antigo> <commit-novo>
```

---

## 14. Configurar um repositório remoto extra

Adição de um repositório remoto adicional:
```bash
git remote add upstream https://github.com/outro-repo.git
```

Busca de alterações no remoto adicional:
```bash
git fetch upstream
```

Mesclagem das alterações na branch atual:
```bash
git merge upstream/main
```

---

## Automatizando Git com Função Personalizada no Linux (usando `vi`)

Esta seção apresenta um fluxo para criação de uma função de automação de comandos Git no shell.

### 1. Criar a pasta de funções

```bash
mkdir -p ~/functions
```

---

### 2. Criar o arquivo com a função usando `vi`

```bash
vi ~/functions/functions
```

Dentro do `vi`, seguir os passos:

1. Pressionar `i` para entrar no modo de inserção.  
2. Inserir a função a seguir:
   ```bash
   function d() {
     git add .
     git commit -m "$1"
     git push
   }
   ```
3. Pressionar `ESC` para sair do modo de inserção.  
4. Digitar `:wq` e pressionar `ENTER` para salvar e sair.

---

### 3. Editar o `.bashrc` com `vi`

```bash
vi ~/.bashrc
```

No editor:

1. Pressionar `G` para ir ao final do arquivo.  
2. Pressionar `o` para adicionar uma nova linha.  
3. Inserir a linha:
   ```bash
   source ~/functions/functions
   ```
4. Pressionar `ESC`.  
5. Digitar `:wq` e pressionar `ENTER` para salvar e sair.

---

### 4. Recarregar o terminal

```bash
source ~/.bashrc
```

---

### 5. Testar a função

Dentro de um repositório Git inicializado, executar:
```bash
d
```

A função executa internamente:
```bash
git add .
git commit -m "automatic commit"
git push
```

---

Este conjunto de comandos e configurações oferece uma base prática para uso cotidiano de Git e GitHub, desde operações iniciais até pequenos fluxos de automação no terminal Linux.
