# 50 Comandos Essenciais do Linux

## Parte 1 – Gerenciamento de Arquivos e Diretórios (Passo a Passo)

Nesta primeira parte é criada uma estrutura básica de arquivos e diretórios para praticar todos os comandos seguintes.

### Passo 1: Criar uma pasta de trabalho
```bash
mkdir -p ~/lab-linux/arquivos
cd ~/lab-linux
```
- `mkdir -p` cria a pasta principal e subpastas se necessário.
- `cd` altera o diretório de trabalho.

### Passo 2: Navegar e listar conteúdo
```bash
ls
ls -l
ls -a
ls -lh
```
- `ls`: lista arquivos.
- `ls -l`: mostra detalhes como permissões e tamanho.
- `ls -a`: exibe arquivos ocultos.
- `ls -lh`: mostra tamanhos legíveis (KB, MB).

### Passo 3: Criar arquivos vazios e navegar entre pastas
```bash
touch arquivos/um.txt
mkdir -p arquivos/subpasta
cd arquivos
pwd
```
- `touch` cria arquivo vazio.
- `mkdir` cria diretório.
- `cd` entra na pasta.
- `pwd` mostra o caminho completo do diretório atual.

### Passo 4: Voltar um nível e criar mais pastas
```bash
cd ..
mkdir backups
```
- `cd ..` retorna ao diretório pai.
- `mkdir backups` cria um novo diretório chamado `backups`.

### Passo 5: Remover diretórios vazios
```bash
mkdir temp
rmdir temp
```
- `rmdir` remove diretórios vazios.

### Passo 6: Remover arquivos e pastas (com cuidado!)
```bash
rm arquivos/um.txt
rm -r arquivos/subpasta
rm -rf backups
```
- `rm` remove arquivos.
- `rm -r` remove diretórios de forma recursiva.
- `rm -rf` força a remoção recursiva sem confirmação (uso exige cautela).

### Passo 7: Criar dois arquivos e copiá-los
```bash
mkdir arquivos
cd arquivos
touch a.txt b.txt
cp a.txt copia_de_a.txt
cp -r ../arquivos ../arquivos_backup
```
- `cp` copia arquivos.
- `cp -r` copia diretórios de forma recursiva.

### Passo 8: Mover e renomear arquivos
```bash
mv b.txt renomeado.txt
mv renomeado.txt ../
```
- `mv` move ou renomeia arquivos, dependendo do contexto de uso.

### Passo 9: Verificar tipo de arquivo
```bash
file a.txt
```
- `file` mostra o tipo de conteúdo identificado no arquivo.

---

## ✅ Conclusão da Parte 1

Ao final desta etapa é estabelecida uma base funcional para continuar os testes de conteúdo de arquivos e sua manipulação com segurança. Todos os comandos são executados sobre arquivos criados dentro da estrutura de prática.

Na parte seguinte são explorados comandos como `cat`, `less`, `head`, `tail`, `grep`, `sed`, `awk` etc., utilizando os arquivos já existentes e outros criados conforme a necessidade.

---

## Parte 2 – Manipulação de Conteúdo de Arquivos (Passo a Passo)

### Passo 1: Preparar arquivos com conteúdo
```bash
cd ~/lab-linux
cd arquivos
echo -e "linha 1\nlinha 2\nlinha 3" > a.txt
echo -e "erro: falha\ninfo: ok\naviso: cuidado" > log.txt
echo -e "nome idade\njoao 30\nmaria 25" > dados.txt
```
- `echo -e` imprime múltiplas linhas, e o operador `>` redireciona a saída para o arquivo, sobrescrevendo o conteúdo existente.

### Passo 2: Visualizar conteúdo com `cat` e `less`
```bash
cat a.txt
less log.txt  # Use q para sair
``]
- `cat` exibe todo o conteúdo de uma vez.
- `less` permite navegação pelo arquivo (setas, rolagem); a tecla `q` encerra a visualização.

### Passo 3: Ver as primeiras e últimas linhas
```bash
head -n 2 log.txt
tail -n 2 log.txt
tail -f log.txt  # Use Ctrl+C para sair
```
- `head` mostra as linhas iniciais.
- `tail` mostra as linhas finais.
- `tail -f` acompanha atualizações em tempo real; `Ctrl+C` interrompe.

### Passo 4: Buscar textos com `grep`
```bash
grep "erro" log.txt
grep -i "AVISO" log.txt
grep -r "joao" .
```
- `grep` procura por padrões de texto.
- `-i` ignora diferenças entre maiúsculas e minúsculas.
- `-r` realiza busca recursiva em subdiretórios.

### Passo 5: Substituir palavras com `sed`
```bash
sed 's/joao/JOÃO/g' dados.txt
```
- `sed` realiza substituições e transformações em texto.
- A expressão `s/antigo/novo/g` substitui todas as ocorrências do padrão.

### Passo 6: Manipular colunas com `awk`
```bash
awk '{print $1}' dados.txt
awk '{print $2}' dados.txt
```
- `awk` permite manipular colunas de texto, imprimindo campos específicos de cada linha.

### Passo 7: Contar linhas, palavras e bytes com `wc`
```bash
wc -l dados.txt
wc -w dados.txt
wc -c dados.txt
```
- `wc` exibe estatísticas do arquivo:
  - `-l`: número de linhas.
  - `-w`: número de palavras.
  - `-c`: número de bytes.

### Passo 8: Ordenar linhas com `sort`
```bash
sort dados.txt
```
- `sort` organiza as linhas em ordem alfabética ou numérica, dependendo do conteúdo.

### Passo 9: Comparar arquivos com `diff`
```bash
echo -e "nome idade\njoao 30\nmaria 22" > dados_v2.txt
diff dados.txt dados_v2.txt
```
- `diff` compara linha a linha o conteúdo de dois arquivos, mostrando as diferenças.

---

## ✅ Conclusão da Parte 2

Nesta etapa é apresentada a leitura e manipulação de conteúdo de arquivos de texto com comandos fundamentais do terminal. Os arquivos são criados com `echo` e utilizados como base para testes de consulta, filtragem, ordenação e comparação.

Na parte seguinte são abordados comandos de sistema como `top`, `ps`, `kill`, `df`, `uptime` e outros relacionados a monitoramento de recursos.

---

## Parte 3 – Informações e Gerenciamento do Sistema (Passo a Passo)

### Passo 1: Ver informações do sistema
```bash
uname -a
```
- `uname -a` mostra nome do kernel, versão, arquitetura e nome do host.

### Passo 2: Ver processos em tempo real
```bash
top
```
- `top` exibe processos ativos e uso de CPU/memória em tempo real.

### Passo 3: Visualizar processos com mais detalhes
```bash
ps aux
ps aux | grep bash
```
- `ps aux` lista todos os processos do sistema com informações detalhadas.
- O uso de `grep` filtra processos específicos (por exemplo, `bash`).

### Passo 4: Encerrar processos manualmente
```bash
kill 1234
kill -9 1234
```
- `kill` envia um sinal para encerrar um processo pelo PID.
- A opção `-9` força o encerramento imediato.

> Dica: `ps aux | grep nome_do_programa` ajuda a localizar o PID do processo desejado.

### Passo 5: Ver uso de disco e diretórios
```bash
df -h
du -sh ~/lab-linux
```
- `df -h` mostra o uso de disco em todas as partições, em formato legível.
- `du -sh` apresenta o tamanho total de um diretório específico.

### Passo 6: Ver uso de memória e tempo de atividade
```bash
free -m
uptime
```
- `free -m` mostra o uso de memória RAM e swap em MB.
- `uptime` exibe há quanto tempo o sistema está em funcionamento, além da carga média.

### Passo 7: Ver quem está logado no sistema
```bash
who
w
```
- `who` lista usuários logados.
- `w` mostra usuários logados e as atividades de cada um.

### Passo 8: Ver histórico de comandos e reiniciar
```bash
history
sudo shutdown -h now
sudo reboot
```
- `history` apresenta comandos executados anteriormente.
- `shutdown` desliga o sistema.
- `reboot` reinicia o sistema.

---

## ✅ Conclusão da Parte 3

Ao final desta parte são dominados os principais comandos para obter informações do sistema, gerenciar processos, verificar uso de recursos e controlar desligamento e reinicialização. Esses comandos fazem parte das rotinas de administração em Linux.

Na parte seguinte são apresentados comandos de rede como `ping`, `ssh`, `scp`, `curl` e outros.

---

## Parte 4 – Comandos de Rede (Passo a Passo)

### Passo 1: Testar conectividade com `ping`
```bash
ping google.com
```
- `ping` envia pacotes ICMP para testar se um host está acessível e mede o tempo de resposta.
- `Ctrl+C` interrompe o teste.

### Passo 2: Ver informações da interface de rede
```bash
ip addr
ip route
```
- `ip addr` mostra os endereços IP atribuídos às interfaces de rede.
- `ip route` exibe a tabela de rotas utilizada pela máquina.

### Passo 3: Ver portas e conexões abertas
```bash
netstat -tulnp
```
- `netstat -tulnp` mostra portas TCP e UDP abertas e os processos associados.

> Observação: pode ser necessária a instalação do pacote `net-tools` para utilizar `netstat`.

### Passo 4: Conectar em uma máquina remota com `ssh`
```bash
ssh usuario@192.168.1.10
```
- `ssh` estabelece conexão segura com outro computador na rede por meio de criptografia.
- `usuario` e o endereço IP devem ser ajustados conforme o alvo desejado.

### Passo 5: Enviar e receber arquivos com `scp`
```bash
scp arquivo.txt usuario@192.168.1.10:/home/usuario/
scp usuario@192.168.1.10:/home/usuario/arquivo.txt ./
```
- `scp` transfere arquivos de forma segura via SSH.
- No primeiro exemplo, o arquivo é enviado; no segundo, o arquivo é copiado da máquina remota para o diretório atual.

### Passo 6: Baixar arquivos com `wget` e `curl`
```bash
wget https://example.com/arquivo.zip
curl -O https://example.com/arquivo.zip
```
- `wget` e `curl -O` realizam download de arquivos diretamente pela URL.

`curl` também pode ser utilizado para acessar APIs ou testar endpoints:
```bash
curl https://api.github.com
```

---

## ✅ Conclusão da Parte 4

Com esses comandos de rede é possível testar conexões, acessar máquinas remotas, transferir arquivos e baixar recursos da internet. Tais operações são essenciais para administração de sistemas Linux, desenvolvimento e operações em ambientes distribuídos.

Na parte seguinte são abordados comandos relacionados a permissões, propriedade de arquivos e aspectos básicos de segurança no terminal.

---

## Parte 5 – Permissões e Propriedades de Arquivos (Passo a Passo)

### Passo 1: Criar arquivos de teste
```bash
cd ~/lab-linux/arquivos
touch permissao.txt
```
- `touch` cria um novo arquivo vazio chamado `permissao.txt`.

### Passo 2: Ver permissões atuais do arquivo
```bash
ls -l permissao.txt
```
- `ls -l` exibe permissões, proprietário e grupo associados ao arquivo.

### Passo 3: Alterar permissões com `chmod`
```bash
chmod 755 permissao.txt
ls -l permissao.txt
chmod u-x permissao.txt
ls -l permissao.txt
```
- `chmod` define permissões numéricas (por exemplo, 755 = leitura/escrita/execução para o dono, leitura/execução para grupo e outros).
- A opção simbólica `u-x` remove a permissão de execução do usuário proprietário.

### Passo 4: Ver usuário atual e criar um novo (opcional)
```bash
whoami
# sudo adduser testeusuario  # comando opcional para criar um usuário de teste
```
- `whoami` mostra o nome do usuário atualmente autenticado.
- `adduser` cria um novo usuário no sistema (requer privilégios de administrador).

### Passo 5: Alterar dono do arquivo com `chown`
```bash
sudo chown $USER permissao.txt
```
- `chown` altera o proprietário do arquivo para o usuário atual (por meio da variável `$USER`).

### Passo 6: Alterar grupo do arquivo com `chgrp`
```bash
sudo chgrp $(id -gn) permissao.txt
```
- `chgrp` modifica o grupo proprietário do arquivo.
- `id -gn` retorna o nome do grupo principal do usuário atual.

### Passo 7: Combinar `chown` com grupo
```bash
sudo chown $USER:$USER permissao.txt
```
- Combinação de alteração de proprietário e grupo em um único comando.

---

## ✅ Conclusão da Parte 5

Nesta parte são vistos conceitos de segurança básica no Linux, com foco em controle de permissões de leitura, escrita e execução, além de propriedade e grupos. Essa base é fundamental para proteger o sistema e configurar scripts e aplicações de forma adequada.

Na parte seguinte são explorados gerenciadores de pacotes utilizados nas principais distribuições Linux, como Ubuntu, CentOS e Fedora.

---

## Parte 6 – Gerenciamento de Pacotes (Passo a Passo)

### Passo 1: Atualizar lista de pacotes no Ubuntu/Debian (`apt`)
```bash
sudo apt update
```
- `apt update` consulta os repositórios e atualiza a lista de pacotes disponíveis.

### Passo 2: Instalar um pacote com `apt`
```bash
sudo apt install cowsay
```
- `apt install` baixa e instala o pacote especificado. No exemplo, é utilizado o pacote `cowsay`.

### Passo 3: Remover um pacote com `apt`
```bash
sudo apt remove cowsay
```
- `apt remove` desinstala o pacote, mantendo em geral arquivos de configuração.

> Dica: `sudo apt purge` remove também arquivos de configuração do pacote.

### Passo 4: Atualizar pacotes no CentOS/RHEL (`yum`)
```bash
sudo yum update
```
- `yum update` atualiza todos os pacotes do sistema nessas distribuições.

### Passo 5: Instalar pacote com `yum`
```bash
sudo yum install httpd
```
- `yum install` instala um pacote (no exemplo, o servidor web `httpd`).

### Passo 6: Remover pacote com `yum`
```bash
sudo yum remove httpd
```
- `yum remove` desinstala o pacote especificado.

### Passo 7: Usar o `dnf` (Fedora e versões mais recentes do CentOS)
```bash
sudo dnf update
sudo dnf install nano
sudo dnf remove nano
```
- `dnf` é o gerenciador moderno que substitui o `yum` em algumas distribuições, oferecendo desempenho e recursos aprimorados.
- A sintaxe de uso é semelhante à do `yum`.

> Todos esses comandos exigem privilégios administrativos por meio de `sudo`.

---

## ✅ Conclusão da Parte 6

Ao concluir esta parte, são conhecidos os principais gerenciadores de pacotes das distribuições Linux mais comuns. Instalar, atualizar e remover pacotes é atividade essencial para manter o sistema estável, funcional e seguro.

Na parte seguinte são apresentados comandos adicionais e boas práticas para uso do terminal, como `man`, `alias` e formas de trabalhar com histórico e redirecionamentos.

---

## Parte 7 – Comandos Extras e Boas Práticas no Terminal (Passo a Passo)

### Passo 1: Consultar ajuda com o `man`
```bash
man ls
```
- `man` exibe o manual de um comando, com descrição detalhada e todas as opções disponíveis.
- A tecla `q` encerra a leitura do manual.

### Passo 2: Criar atalhos com `alias`
```bash
alias ll='ls -l'
ll
```
- `alias` cria comandos personalizados para facilitar o uso do terminal.
- No exemplo, `ll` passa a executar `ls -l`.

> Observação: para tornar o alias permanente, é necessário adicioná-lo em arquivos de configuração de shell, como `~/.bashrc` ou `~/.zshrc`.

### Passo 3: Ver histórico de comandos
```bash
history | tail -n 5
```
- `history` lista comandos executados anteriormente.
- O uso combinado com `tail -n 5` mostra apenas as últimas cinco entradas.

### Passo 4: Executar comandos como administrador com `sudo`
```bash
sudo whoami
```
- `sudo` executa comandos com privilégios de administrador (root).
- `whoami` retorna o nome do usuário sob o qual o comando está sendo executado.

### Passo 5: Usar autocompletar com Tab
A funcionalidade de autocompletar pode ser utilizada digitando parte do nome de um comando ou arquivo e pressionando `Tab`:

```bash
cd ~/lab[TAB]       # completa para lab-linux
```

### Passo 6: Redirecionar saída de comandos
```bash
ls -l > listagem.txt
cat listagem.txt
```
- O operador `>` redireciona a saída padrão para um arquivo, sobrescrevendo o conteúdo.
- O operador `>>` adiciona a saída ao final do arquivo, preservando o conteúdo existente.

### Passo 7: Usar pipes para combinar comandos
```bash
ps aux | grep bash
```
- O símbolo `|` (pipe) envia a saída de um comando como entrada para outro.
- No exemplo, a listagem de processos gerada por `ps aux` é filtrada por `grep bash`.

---

## ✅ Conclusão da Parte 7

Com os comandos e práticas apresentados nesta parte, o uso do terminal torna-se mais ágil, organizado e eficiente. A combinação de histórico, aliases, redirecionamentos e pipes estabelece uma base sólida para o domínio do ambiente Linux em atividades do dia a dia, administração de sistemas e automação de tarefas.
