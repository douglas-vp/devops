# 5. Gerenciamento de commits

Commits são pontos de registro no histórico do projeto. O gerenciamento de commits permite criar, consultar, revisar, desfazer e navegar entre versões do código.

---

## 5.1 Criar commit com mensagem

```bash
git commit -m "Adiciona tela de login"
```

A flag `-m` permite informar a mensagem diretamente no terminal.

---

## 5.2 Criar commit adicionando arquivos modificados

```bash
git commit -a -m "Atualiza lógica de autenticação"
```

Esse comando adiciona automaticamente arquivos já rastreados e cria o commit.

Importante: arquivos novos ainda não rastreados não entram nesse commit. Para arquivos novos, use antes:

```bash
git add arquivo
```

---

## 5.3 Consultar histórico com `git log`

```bash
git log
```

Exemplo de saída:

```bash
commit 9fceb02a1b4c
Author: Douglas Pontes <douglas@email.com>
Date:   Mon Apr 27 10:00:00 2026 -0300

    Adiciona README inicial
```

---

## 5.4 Consultar alterações detalhadas com `git log -p`

```bash
git log -p
```

Esse comando mostra o histórico de commits e as alterações realizadas em cada commit.

---

## 5.5 Acessar um commit específico com `git checkout`

```bash
git checkout HASH
```

Exemplo:

```bash
git checkout 9fceb02
```

Esse comando coloca o repositório em um estado chamado **detached HEAD**, usado para inspecionar versões antigas.

Para voltar para a branch principal:

```bash
git checkout main
```

---

## 5.6 Desfazer o último commit mantendo alterações com `reset --soft`

```bash
git reset --soft HEAD~1
```

Esse comando desfaz o último commit, mas mantém as alterações preparadas na área de staging.

Fluxo:

```bash
git reset --soft HEAD~1
git commit -m "Nova mensagem do commit"
```

---

## 5.7 Descartar alterações com `reset --hard`

```bash
git reset --hard
```

Esse comando descarta alterações locais não commitadas e retorna os arquivos ao último commit.

Também é possível voltar para um commit específico:

```bash
git reset --hard HASH
```

Atenção: esse comando pode apagar alterações locais de forma definitiva.

---

## 5.8 Diferença entre `reset --soft` e `reset --hard`

| Comando | O que acontece |
|---|---|
| `git reset --soft HEAD~1` | Remove o último commit e mantém alterações no staging |
| `git reset --hard` | Descarta alterações locais não commitadas |
| `git reset --hard HASH` | Volta para um commit específico e descarta alterações posteriores localmente |

---

## 5.9 Tabela resumo

| Comando | Função |
|---|---|
| `git commit -m "mensagem"` | Cria commit com mensagem |
| `git commit -a -m "mensagem"` | Adiciona arquivos rastreados modificados e cria commit |
| `git log` | Mostra histórico de commits |
| `git log -p` | Mostra histórico com alterações detalhadas |
| `git checkout HASH` | Acessa um commit específico para inspeção |
| `git reset --soft HEAD~1` | Desfaz último commit mantendo alterações |
| `git reset --hard` | Descarta alterações locais |
