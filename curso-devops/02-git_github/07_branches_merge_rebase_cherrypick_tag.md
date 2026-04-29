# 7. Branches, merge, rebase, cherry-pick e tags

Branches permitem criar linhas paralelas de desenvolvimento. Com elas, é possível trabalhar em novas funcionalidades sem alterar diretamente a branch principal.

---

## 7.1 Ver branches existentes

```bash
git branch
```

A branch atual aparece marcada com `*`.

Exemplo:

```bash
* main
  feature/login
```

---

## 7.2 Criar uma branch

```bash
git branch feature/login
```

Esse comando cria a branch, mas não muda para ela.

---

## 7.3 Trocar de branch com `git checkout`

```bash
git checkout feature/login
```

Voltar para a branch principal:

```bash
git checkout main
```

---

## 7.4 Criar e acessar branch ao mesmo tempo

```bash
git checkout -b feature/login
```

Esse comando equivale a:

```bash
git branch feature/login
git checkout feature/login
```

---

## 7.5 Renomear branch

Renomear a branch atual:

```bash
git branch -m novo-nome
```

Renomear uma branch específica:

```bash
git branch -m nome-antigo nome-novo
```

---

## 7.6 Remover branch

Remover branch já integrada:

```bash
git branch -d feature/login
```

Forçar remoção de branch:

```bash
git branch -D feature/login
```

A opção `-D` deve ser usada com cuidado, pois remove a branch mesmo que ela contenha commits não integrados.

---

## 7.7 Merge

O **merge** une alterações de uma branch em outra.

Exemplo: aplicar alterações de `feature/login` na `main`.

```bash
git checkout main
git merge feature/login
```

---

## 7.8 Rebase

O **rebase** reaplica commits de uma branch sobre outra base.

Exemplo:

```bash
git checkout feature/login
git rebase main
```

Uso comum:

- atualizar uma branch de funcionalidade com a base mais recente da `main`;
- manter histórico mais linear;
- reduzir commits de merge desnecessários.

Atenção: evite fazer rebase em branches compartilhadas sem alinhamento com a equipe.

---

## 7.9 Diferença entre merge e rebase

| Operação | Característica |
|---|---|
| Merge | Preserva o histórico original e cria commit de merge quando necessário |
| Rebase | Reorganiza commits e deixa o histórico mais linear |

---

## 7.10 Cherry-pick

O **cherry-pick** aplica um commit específico em outra branch.

```bash
git cherry-pick HASH
```

Exemplo:

```bash
git checkout main
git cherry-pick 9fceb02
```

Uso comum:

- aplicar uma correção específica em outra branch;
- reaproveitar um commit sem fazer merge completo;
- mover uma alteração pontual para uma branch de release ou hotfix.

---

## 7.11 Tags

Tags são marcações usadas para identificar versões específicas do projeto.

Exemplo comum:

```bash
v1.0.0
v1.1.0
v2.0.0
```

---

## 7.12 Criar tag anotada

```bash
git tag -a v1.0.0 -m "Versão 1.0.0"
```

---

## 7.13 Criar tag em commit específico

```bash
git tag -a v1.0.0 HASH -m "Versão 1.0.0"
```

Exemplo:

```bash
git tag -a v1.0.0 9fceb02 -m "Versão inicial estável"
```

---

## 7.14 Exibir detalhes de uma tag

```bash
git show v1.0.0
```

---

## 7.15 Listar tags

```bash
git tag
```

---

## 7.16 Tabela resumo

| Comando | Função |
|---|---|
| `git branch` | Lista branches locais |
| `git branch nome` | Cria uma branch |
| `git checkout nome` | Troca para uma branch |
| `git checkout -b nome` | Cria e acessa uma branch |
| `git branch -m novo-nome` | Renomeia a branch atual |
| `git branch -d nome` | Remove branch integrada |
| `git branch -D nome` | Força remoção de branch |
| `git merge branch` | Une uma branch à branch atual |
| `git rebase branch` | Reaplica commits sobre outra base |
| `git cherry-pick HASH` | Aplica um commit específico |
| `git tag -a v1.0.0 -m "mensagem"` | Cria tag anotada |
| `git show tag` | Mostra detalhes da tag |
