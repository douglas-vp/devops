# Navegação, Arquivos e Permissões no Linux

### 3. Caminhos absolutos e relativos

#### Caminho absoluto

É o caminho completo a partir da raiz `/`.

Exemplo:

```bash
/home/douglas/Documentos/arquivo.txt
```

#### Caminho relativo

É o caminho a partir do diretório atual.

Exemplo:

```bash
Documentos/arquivo.txt
```

Se você estiver em:

```bash
/home/douglas
```

Então o caminho relativo:

```bash
Documentos/arquivo.txt
```

equivale a:

```bash
/home/douglas/Documentos/arquivo.txt
```

---

### 4. Diretório atual e diretório anterior

#### Ver o diretório atual

```bash
pwd
```

#### Ir para outro diretório

```bash
cd /home/douglas
```

#### Voltar um nível

```bash
cd ..
```

### Ir para a home do usuário

```bash
cd ~
```

ou:

```bash
cd
```

#### Ir para o diretório raiz

```bash
cd /
```

---

### 5. Permissões no Linux

Cada arquivo e diretório possui permissões para três grupos:

```bash
usuário dono
grupo
outros usuários
```

As permissões principais são:

```bash
r = read    # leitura
w = write   # escrita
x = execute # execução
```

Exemplo de permissões:

```bash
-rw-r--r--
```

Interpretação:

```bash
-     arquivo comum
rw-   dono pode ler e escrever
r--   grupo pode apenas ler
r--   outros podem apenas ler
```

Exemplo para diretório:

```bash
drwxr-xr-x
```

Interpretação:

```bash
d     diretório
rwx   dono pode ler, escrever e acessar
r-x   grupo pode ler e acessar
r-x   outros podem ler e acessar
```

---

### 6. Comandos básicos para navegar e manipular arquivos

#### Listar arquivos

```bash
ls
```

Listar com detalhes:

```bash
ls -la
```

#### Criar diretório

```bash
mkdir nome_da_pasta
```

#### Criar arquivo vazio

```bash
touch arquivo.txt
```

#### Copiar arquivo

```bash
cp origem destino
```

Exemplo:

```bash
cp arquivo.txt /home/douglas/Documentos/
```

#### Mover ou renomear arquivo

```bash
mv origem destino
```

Exemplo para mover:

```bash
mv arquivo.txt /home/douglas/Documentos/
```

Exemplo para renomear:

```bash
mv antigo.txt novo.txt
```

#### Remover arquivo

```bash
rm arquivo.txt
```

#### Remover diretório vazio

```bash
rmdir pasta
```

#### Remover diretório com conteúdo

```bash
rm -r pasta
```

Use com cuidado.

---
