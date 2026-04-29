# 6. Ignorando arquivos com `.gitignore`

O arquivo `.gitignore` informa ao Git quais arquivos e pastas devem ser ignorados.

Ele é usado para evitar que arquivos temporários, dependências, credenciais, caches e configurações locais sejam versionados.

---

## 6.1 Criar arquivo `.gitignore`

```bash
touch .gitignore
```

Editar com Nano:

```bash
nano .gitignore
```

---

## 6.2 Exemplo básico de `.gitignore`

```gitignore
# Ambientes virtuais Python
.venv/
venv/

# Arquivos de cache Python
__pycache__/
*.pyc

# Variáveis de ambiente
.env

# Logs
*.log

# Pastas de build
dist/
build/

# Configurações de IDE
.vscode/
.idea/
```

---

## 6.3 Ignorar arquivos específicos

```gitignore
config.local.json
senha.txt
```

---

## 6.4 Ignorar arquivos por extensão

```gitignore
*.log
*.tmp
*.bak
```

---

## 6.5 Ignorar pastas

```gitignore
node_modules/
.venv/
__pycache__/
```

---

## 6.6 Negar uma regra com `!`

É possível ignorar todos os arquivos de um tipo, mas manter uma exceção.

```gitignore
*.log
!important.log
```

Nesse exemplo, todos os arquivos `.log` são ignorados, exceto `important.log`.

---

## 6.7 Arquivo já versionado não é ignorado automaticamente

Se um arquivo já foi commitado, adicioná-lo ao `.gitignore` não remove o arquivo do controle do Git.

Para remover do rastreamento sem apagar do disco:

```bash
git rm --cached arquivo
```

Exemplo:

```bash
git rm --cached .env
```

Depois, criar um commit:

```bash
git add .gitignore
git commit -m "Atualiza gitignore"
```

---

## 6.8 Verificar arquivos ignorados

```bash
git status --ignored
```

Esse comando mostra arquivos ignorados pelo `.gitignore`.

---

## 6.9 Tabela resumo

| Regra ou comando | Função |
|---|---|
| `.env` | Ignora arquivo específico |
| `*.log` | Ignora todos os arquivos com extensão `.log` |
| `pasta/` | Ignora uma pasta inteira |
| `# comentário` | Adiciona comentário |
| `!arquivo.log` | Cria exceção para arquivo ignorado |
| `git rm --cached arquivo` | Remove arquivo do rastreamento sem apagar localmente |
