# 10. Rastreamento com `git log`

O `git log` permite consultar o histórico do repositório. Ele mostra commits, autores, datas, mensagens e alterações.

É uma ferramenta essencial para rastrear decisões, investigar problemas e entender a evolução do projeto.

---

## 10.1 Histórico completo

```bash
git log
```

Mostra os commits em ordem cronológica reversa, do mais recente para o mais antigo.

---

## 10.2 Histórico resumido com `--oneline`

```bash
git log --oneline
```

Observação: o comando correto é `--oneline`, com uma letra `e` em `line`.

Exemplo:

```bash
9fceb02 Adiciona README inicial
5a1c921 Corrige validação de login
2b6d113 Atualiza documentação
```

---

## 10.3 Histórico com estatísticas

```bash
git log --stat
```

Mostra arquivos alterados e quantidade de linhas adicionadas ou removidas.

---

## 10.4 Histórico com alterações detalhadas

```bash
git log -p
```

Mostra o conteúdo alterado em cada commit.

---

## 10.5 Limitar quantidade de commits

```bash
git log -n 2
```

Mostra apenas os dois commits mais recentes.

Outro exemplo:

```bash
git log -n 5 --oneline
```

---

## 10.6 Visualizar histórico em gráfico

```bash
git log --graph
```

Exibir gráfico resumido:

```bash
git log --graph --oneline
```

Exemplo:

```bash
* 9fceb02 Adiciona tela de login
* 5a1c921 Atualiza README
| * 2b6d113 Cria branch feature
|/
* 1a2b3c4 Commit inicial
```

---

## 10.7 Filtrar por autor

```bash
git log --author="Douglas"
```

Também é possível combinar com `--oneline`:

```bash
git log --author="Douglas" --oneline
```

---

## 10.8 Filtrar por data

Commits após uma data:

```bash
git log --after="2026-04-01"
```

Commits antes de uma data:

```bash
git log --before="2026-04-30"
```

Combinar intervalo:

```bash
git log --after="2026-04-01" --before="2026-04-30"
```

---

## 10.9 Combinar filtros

```bash
git log --author="Douglas" --after="2026-04-01" --oneline
```

```bash
git log --graph --oneline --all
```

```bash
git log -n 3 --stat
```

---

## 10.10 Investigar alterações de um arquivo específico

```bash
git log -- README.md
```

Com detalhes:

```bash
git log -p -- README.md
```

---

## 10.11 Tabela resumo

| Comando | Função |
|---|---|
| `git log` | Mostra histórico completo |
| `git log --oneline` | Mostra histórico resumido em uma linha por commit |
| `git log --stat` | Mostra estatísticas de arquivos alterados |
| `git log -p` | Mostra alterações detalhadas dos commits |
| `git log -n 2` | Mostra os dois commits mais recentes |
| `git log --graph` | Mostra histórico em formato gráfico |
| `git log --graph --oneline` | Mostra gráfico resumido |
| `git log --author="Nome"` | Filtra commits por autor |
| `git log --after="YYYY-MM-DD"` | Filtra commits após uma data |
| `git log --before="YYYY-MM-DD"` | Filtra commits antes de uma data |
| `git log -- arquivo` | Mostra histórico de um arquivo específico |

---

## 10.12 Comando recomendado para visão geral

```bash
git log --graph --oneline --all
```

Esse comando mostra uma visão resumida das branches e commits do repositório.
