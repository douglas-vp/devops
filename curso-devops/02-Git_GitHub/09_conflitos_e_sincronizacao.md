# 9. Conflitos e sincronização com repositório remoto

Conflitos ocorrem quando o Git não consegue combinar automaticamente alterações feitas no mesmo trecho de um arquivo.

Isso é comum quando duas pessoas alteram a mesma linha ou quando uma branch local está desatualizada em relação ao remoto.

---

## 9.1 Atualizar branch local com `git pull`

```bash
git pull
```

Esse comando busca alterações do remoto e tenta integrá-las à branch atual.

---

## 9.2 Configurar estratégia de pull com merge

```bash
git config pull.rebase false
```

Essa configuração informa que o `git pull` deve usar merge em vez de rebase.

Também é possível configurar globalmente:

```bash
git config --global pull.rebase false
```

---

## 9.3 Quando ocorre conflito

Exemplo de arquivo em conflito:

```text
<<<<<<< HEAD
Texto da branch local
=======
Texto vindo do repositório remoto
>>>>>>> origin/main
```

Significado:

| Marcador | Significado |
|---|---|
| `<<<<<<< HEAD` | Início da alteração local |
| `=======` | Separação entre versões |
| `>>>>>>> origin/main` | Fim da alteração remota |

---

## 9.4 Resolver conflito manualmente

Abra o arquivo, escolha a versão correta e remova os marcadores.

Antes:

```text
<<<<<<< HEAD
porta=8000
=======
porta=8080
>>>>>>> origin/main
```

Depois:

```text
porta=8080
```

---

## 9.5 Finalizar resolução de conflito

Após corrigir o arquivo:

```bash
git status
git add arquivo_com_conflito
git commit -m "Resolve conflito de configuração"
```

---

## 9.6 Fluxo recomendado antes de começar a trabalhar

```bash
git checkout main
git pull
git checkout -b feature/nova-funcionalidade
```

Esse fluxo reduz a chance de criar uma branch a partir de uma base antiga.

---

## 9.7 Fluxo recomendado antes de enviar alterações

```bash
git status
git pull
git push
```

Se houver conflito durante o `git pull`, resolva o conflito antes de executar `git push`.

---

## 9.8 Usar fetch antes do merge

```bash
git fetch
git branch -r
git merge origin/main
```

Esse fluxo é útil quando se deseja visualizar o estado remoto antes de integrar alterações.

---

## 9.9 Diferença entre `pull`, `fetch` e `merge`

| Comando | Função |
|---|---|
| `git fetch` | Busca alterações remotas sem integrar |
| `git merge` | Integra alterações de outra branch à branch atual |
| `git pull` | Executa `fetch` seguido de integração |

---

## 9.10 Exemplo de sincronização com branch remota

```bash
git checkout feature/login
git pull
git add .
git commit -m "Atualiza login"
git push
```

---

## 9.11 Tabela resumo

| Comando | Função |
|---|---|
| `git config pull.rebase false` | Define pull com merge no repositório atual |
| `git config --global pull.rebase false` | Define pull com merge para todos os repositórios do usuário |
| `git pull` | Busca e integra alterações do remoto |
| `git fetch` | Busca alterações sem integrar |
| `git branch -r` | Lista branches remotas |
| `git merge origin/main` | Integra a branch remota `main` à branch atual |
| `git add arquivo` | Marca conflito como resolvido após edição |
| `git commit -m "mensagem"` | Finaliza resolução de conflito |
