# 4. Gerenciamento de arquivos no Git

O gerenciamento de arquivos no Git envolve verificar alterações, adicionar arquivos à área de preparação e criar commits.

O fluxo básico é:

```bash
git status
git add .
git commit -m "Mensagem do commit"
```

---

## 4.1 Estados dos arquivos no Git

| Estado | Significado |
|---|---|
| Untracked | Arquivo novo ainda não rastreado pelo Git |
| Modified | Arquivo rastreado que foi alterado |
| Staged | Arquivo preparado para entrar no próximo commit |
| Committed | Arquivo salvo no histórico do Git |

---

## 4.2 Verificar estado com `git status`

```bash
git status
```

Esse comando mostra arquivos novos, arquivos modificados, arquivos preparados para commit, branch atual e relação com o repositório remoto, quando houver.

Exemplo:

```bash
On branch main
Untracked files:
  README.md
```

---

## 4.3 Adicionar arquivos com `git add`

Adicionar um arquivo específico:

```bash
git add README.md
```

Adicionar todos os arquivos modificados e novos:

```bash
git add .
```

O comando `git add .` envia as alterações para a área de preparação, chamada de **staging area**.

---

## 4.4 Criar commit

```bash
git commit -m "Adiciona documentação inicial"
```

A mensagem deve explicar, de forma objetiva, o que foi alterado.

Exemplos:

```bash
git commit -m "Adiciona README do projeto"
git commit -m "Corrige validação do formulário de login"
git commit -m "Atualiza configuração do Docker Compose"
```

---

## 4.5 Fluxo prático completo

```bash
echo "# Meu Projeto" > README.md
git status
git add README.md
git status
git commit -m "Adiciona README inicial"
```

---

## 4.6 Cuidados com `git add .`

O comando `git add .` adiciona muitas alterações de uma vez.

Antes de usá-lo, recomenda-se executar:

```bash
git status
```

Assim, é possível verificar se arquivos sensíveis, temporários ou desnecessários não serão enviados ao commit.

---

## 4.7 Tabela resumo

| Comando | Função |
|---|---|
| `git status` | Mostra o estado dos arquivos |
| `git add arquivo` | Adiciona um arquivo à área de preparação |
| `git add .` | Adiciona todas as alterações da pasta atual |
| `git commit -m "mensagem"` | Cria um commit com mensagem curta |
