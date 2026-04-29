# Introdução ao Git — Índice de Aprendizado

Este material organiza os principais conceitos e comandos de Git em seções independentes de aprendizado, com exemplos práticos e tabelas-resumo.

## Organização dos arquivos

| Arquivo | Conteúdo principal |
|---|---|
| `01_introducao_ao_git.md` | Conceitos iniciais, repositório, commit, branch, repositório remoto e modelo de branches |
| `02_instalacao_do_git.md` | Instalação do Git em Linux, Windows e macOS |
| `03_configuracao_inicial_e_primeiro_repositorio.md` | Configuração inicial, herança de configuração e criação do primeiro repositório |
| `04_gerenciamento_de_arquivos.md` | Uso de `git status`, `git add` e `git commit` |
| `05_gerenciamento_de_commits.md` | Histórico, checkout por hash, reset soft e reset hard |
| `06_gitignore.md` | Uso do arquivo `.gitignore` para ignorar arquivos e pastas |
| `07_branches_merge_rebase_cherrypick_tag.md` | Branches, merge, rebase, cherry-pick e tags |
| `08_repositorio_local_e_remoto_github.md` | GitHub, SSH, remote, push, clone, pull e fetch |
| `09_conflitos_e_sincronizacao.md` | Conflitos, estratégias de pull e sincronização entre branches |
| `10_rastreamento_e_git_log.md` | Comandos de rastreamento com `git log` e filtros de histórico |

## Sequência recomendada de estudo

1. Entender o que é Git e como o controle de versão funciona.
2. Instalar o Git no sistema operacional utilizado.
3. Configurar nome, e-mail, editor padrão e branch inicial.
4. Criar o primeiro repositório local com `git init`.
5. Versionar arquivos com `git status`, `git add` e `git commit`.
6. Consultar e manipular histórico de commits.
7. Criar e gerenciar branches.
8. Trabalhar com merge, rebase, cherry-pick e tags.
9. Conectar o repositório local ao GitHub.
10. Usar `push`, `pull`, `fetch` e resolver conflitos.

## Convenções usadas nos exemplos

| Termo | Significado |
|---|---|
| `projeto-git` | Nome de exemplo para uma pasta de projeto |
| `main` | Branch principal do projeto |
| `develop` | Branch de desenvolvimento, quando usada |
| `feature/login` | Branch de exemplo para desenvolvimento de funcionalidade |
| `origin` | Nome padrão do repositório remoto |
| `HASH` | Identificador de um commit |
