# 8. Repositório local e remoto com GitHub

Um repositório local fica na máquina do desenvolvedor. Um repositório remoto fica hospedado em uma plataforma externa, como GitHub.

A integração entre os dois permite sincronizar código, compartilhar alterações e colaborar em equipe.

---

## 8.1 Criando um repositório no GitHub

Fluxo comum:

1. Acessar o GitHub.
2. Criar um novo repositório.
3. Definir nome, descrição e visibilidade.
4. Não criar README automaticamente se o projeto local já possuir commits.
5. Copiar a URL do repositório.

Exemplo de URL SSH:

```bash
git@github.com:usuario/projeto.git
```

---

## 8.2 SSH no GitHub

SSH permite autenticar no GitHub usando chave criptográfica, sem digitar senha a cada operação.

Verificar se já existe chave SSH:

```bash
ls -la ~/.ssh
```

Gerar chave SSH:

```bash
ssh-keygen -t ed25519 -C "douglas@email.com"
```

Iniciar agente SSH:

```bash
eval "$(ssh-agent -s)"
```

Adicionar chave ao agente:

```bash
ssh-add ~/.ssh/id_ed25519
```

Exibir chave pública:

```bash
cat ~/.ssh/id_ed25519.pub
```

A chave pública deve ser cadastrada no GitHub em **Settings > SSH and GPG keys**.

Testar conexão:

```bash
ssh -T git@github.com
```

---

## 8.3 Adicionar repositório local no GitHub

Adicionar o remoto chamado `origin`:

```bash
git remote add origin git@github.com:usuario/projeto.git
```

Renomear a branch principal para `main`:

```bash
git branch -M main
```

Enviar primeira vez para o remoto:

```bash
git push -u origin main
```

A opção `-u` define o rastreamento entre a branch local e a branch remota.

---

## 8.4 Ver repositórios remotos configurados

```bash
git remote -v
```

Exemplo:

```bash
origin  git@github.com:usuario/projeto.git (fetch)
origin  git@github.com:usuario/projeto.git (push)
```

---

## 8.5 Clonar um repositório

```bash
git clone git@github.com:usuario/projeto.git
```

Esse comando baixa o repositório remoto para a máquina local.

---

## 8.6 Trabalhando com repositório remoto

Criar branch local:

```bash
git checkout -b feature/login
```

Enviar branch para o remoto pela primeira vez:

```bash
git push --set-upstream origin feature/login
```

Forma equivalente:

```bash
git push -u origin feature/login
```

---

## 8.7 Enviar alterações para o remoto

```bash
git push
```

Esse comando envia commits locais para a branch remota configurada.

---

## 8.8 Trazer alterações do remoto

```bash
git pull
```

O `git pull` busca alterações do remoto e tenta integrá-las à branch local.

---

## 8.9 Buscar alterações sem integrar

```bash
git fetch
```

O `git fetch` baixa informações do remoto, mas não altera automaticamente os arquivos da branch atual.

---

## 8.10 Listar branches remotas

```bash
git branch -r
```

Exemplo:

```bash
origin/main
origin/develop
origin/feature/login
```

---

## 8.11 Integrar alterações baixadas com fetch

```bash
git fetch
git merge origin/main
```

Esse fluxo permite revisar primeiro o que veio do remoto antes de integrar.

---

## 8.12 Fluxo completo para publicar repositório local

```bash
git init
git add .
git commit -m "Adiciona versão inicial"
git remote add origin git@github.com:usuario/projeto.git
git branch -M main
git push -u origin main
```

---

## 8.13 Tabela resumo

| Comando | Função |
|---|---|
| `git remote add origin URL` | Adiciona repositório remoto |
| `git remote -v` | Lista remotos configurados |
| `git branch -M main` | Renomeia branch principal para `main` |
| `git push -u origin main` | Envia branch local e cria rastreamento remoto |
| `git clone URL` | Clona repositório remoto |
| `git push --set-upstream origin branch` | Publica branch local no remoto |
| `git pull` | Busca e integra alterações remotas |
| `git push` | Envia commits locais para o remoto |
| `git fetch` | Busca informações do remoto sem integrar |
| `git branch -r` | Lista branches remotas |
