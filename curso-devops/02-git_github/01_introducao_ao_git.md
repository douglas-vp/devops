# 1. Introdução ao Git

O **Git** é um sistema de controle de versão distribuído. Ele permite registrar alterações em arquivos, acompanhar o histórico de desenvolvimento, criar versões paralelas do projeto e sincronizar o código com repositórios remotos, como GitHub, GitLab ou Bitbucket.

Em vez de salvar várias cópias manuais de um projeto, como `projeto_final`, `projeto_final_corrigido` e `projeto_final_versao_2`, o Git registra cada alteração de forma estruturada por meio de commits.

---

## 1.1 O que é controle de versão

Controle de versão é o processo de registrar mudanças em arquivos ao longo do tempo.

Com ele, é possível:

- consultar o histórico de alterações;
- identificar quem alterou um arquivo;
- recuperar versões anteriores;
- trabalhar em equipe no mesmo projeto;
- criar branches para testar funcionalidades sem afetar a versão principal.

---

## 1.2 Repositório

Um **repositório** é uma pasta controlada pelo Git.

Ele contém:

- os arquivos do projeto;
- o histórico de alterações;
- as branches;
- as configurações internas do Git.

Quando uma pasta passa a ser controlada pelo Git, ela recebe um diretório oculto chamado `.git`.

Exemplo:

```bash
projeto-git/
├── .git/
├── README.md
└── app.py
```

O diretório `.git` armazena os dados internos do controle de versão.

---

## 1.3 Commit

Um **commit** é um registro de alteração no histórico do projeto.

Ele representa um ponto salvo do desenvolvimento.

Exemplo:

```bash
git commit -m "Adiciona arquivo README"
```

Um commit normalmente contém:

| Informação | Descrição |
|---|---|
| Hash | Identificador único do commit |
| Autor | Pessoa que realizou o commit |
| Data | Data e hora da alteração |
| Mensagem | Descrição do que foi alterado |
| Alterações | Arquivos modificados, adicionados ou removidos |

---

## 1.4 Branch

Uma **branch** é uma linha paralela de desenvolvimento.

Ela permite desenvolver funcionalidades, correções ou experimentos sem alterar diretamente a branch principal.

Exemplo:

```bash
git branch feature/login
```

Fluxo comum:

```bash
main
 └── feature/login
```

A branch `main` mantém a versão principal, enquanto `feature/login` recebe alterações relacionadas à funcionalidade de login.

---

## 1.5 Modelo de branches

O modelo de branches define como as branches são organizadas dentro do projeto.

Um modelo simples pode usar:

| Branch | Finalidade |
|---|---|
| `main` | Versão principal e estável |
| `develop` | Versão de desenvolvimento integrada |
| `feature/nome` | Desenvolvimento de nova funcionalidade |
| `fix/nome` | Correção de erro |
| `hotfix/nome` | Correção urgente em produção |
| `release/versao` | Preparação de uma nova versão |

Exemplo de organização:

```bash
main
├── develop
│   ├── feature/login
│   ├── feature/dashboard
│   └── fix/erro-validacao
└── hotfix/correcao-producao
```

---

## 1.6 Repositório remoto

Um **repositório remoto** é uma cópia do projeto hospedada em um servidor externo.

Exemplos de plataformas:

- GitHub;
- GitLab;
- Bitbucket;
- Azure Repos.

O repositório remoto permite:

- compartilhar código com a equipe;
- manter backup do projeto;
- abrir pull requests;
- revisar código;
- integrar com pipelines de CI/CD.

Exemplo de URL SSH do GitHub:

```bash
git@github.com:usuario/projeto.git
```

---

## 1.7 Diferença entre Git e GitHub

| Ferramenta | Função |
|---|---|
| Git | Sistema de controle de versão usado localmente |
| GitHub | Plataforma online para hospedar repositórios Git |

O Git funciona mesmo sem GitHub. O GitHub é uma plataforma que recebe e organiza repositórios Git na nuvem.

---

## 1.8 Resumo prático

| Conceito | Explicação |
|---|---|
| Repositório | Pasta controlada pelo Git |
| Commit | Registro de uma alteração no histórico |
| Branch | Linha paralela de desenvolvimento |
| Merge | União de alterações entre branches |
| Rebase | Reaplicação de commits sobre outra base |
| Tag | Marcação de uma versão específica |
| Remoto | Repositório hospedado fora da máquina local |
