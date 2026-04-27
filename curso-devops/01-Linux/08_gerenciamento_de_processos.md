# Gerenciamento de processos no Linux

Gerenciar processos no Linux significa **visualizar, monitorar, encerrar, priorizar e controlar programas em execução** no sistema.

Um **processo** é qualquer programa ou comando em execução, como navegador, terminal, serviço, script, banco de dados ou aplicação.

---

## 1. Ver processos em execução

### Listar todos os processos

```bash
ps aux
```

Exemplo de saída:

```bash
USER       PID  %CPU %MEM COMMAND
root         1   0.0  0.1 /sbin/init
douglas   2450   2.5  1.8 firefox
douglas   3102   0.1  0.3 bash
```

| Coluna | Significado |
|---|---|
| `USER` | Usuário que iniciou o processo |
| `PID` | Identificador do processo |
| `%CPU` | Uso de CPU |
| `%MEM` | Uso de memória |
| `COMMAND` | Comando ou programa executado |

---

## 2. Filtrar processos com `grep`

### Procurar processo pelo nome

```bash
ps aux | grep nginx
```

Exemplo:

```bash
ps aux | grep python
```

### Evitar que o próprio `grep` apareça no resultado

```bash
ps aux | grep "[p]ython"
```

---

## 3. Monitorar processos em tempo real

### Usando `top`

```bash
top
```

Comandos úteis dentro do `top`:

| Tecla | Função |
|---|---|
| `q` | Sair |
| `k` | Encerrar processo |
| `P` | Ordenar por uso de CPU |
| `M` | Ordenar por uso de memória |

### Usando `htop`

```bash
htop
```

Instalar no Ubuntu/Debian:

```bash
sudo apt install htop
```

No `htop`, é possível navegar com as setas, selecionar processos e encerrar usando `F9`.

---

## 4. Identificar o PID de um processo

O **PID** é o identificador numérico de um processo.

### Usando `pidof`

```bash
pidof nome_do_processo
```

Exemplo:

```bash
pidof nginx
```

### Usando `pgrep`

```bash
pgrep nome_do_processo
```

Exemplo:

```bash
pgrep python
```

Mostrar também o comando:

```bash
pgrep -a python
```

---

## 5. Encerrar processos

### Encerrar processo pelo PID

```bash
kill PID
```

Exemplo:

```bash
kill 2450
```

Esse comando envia o sinal padrão `SIGTERM`, solicitando o encerramento normal do processo.

### Forçar encerramento

```bash
kill -9 PID
```

Exemplo:

```bash
kill -9 2450
```

O sinal `-9` força o encerramento imediato e deve ser usado apenas quando o processo não responde.

### Encerrar processo pelo nome

```bash
pkill nome_do_processo
```

Exemplo:

```bash
pkill firefox
```

### Encerrar todos os processos com determinado nome

```bash
killall nome_do_processo
```

Exemplo:

```bash
killall python
```

---

## 6. Sinais mais comuns

| Sinal | Nome | Função |
|---|---|---|
| `1` | `SIGHUP` | Recarrega ou reinicia configuração em alguns processos |
| `2` | `SIGINT` | Interrompe o processo, semelhante ao `Ctrl + C` |
| `9` | `SIGKILL` | Força o encerramento imediato |
| `15` | `SIGTERM` | Solicita encerramento normal |
| `18` | `SIGCONT` | Continua processo pausado |
| `19` | `SIGSTOP` | Pausa processo |

Encerrar normalmente:

```bash
kill -15 2450
```

Forçar encerramento:

```bash
kill -9 2450
```

---

## 7. Pausar e continuar processos

### Pausar processo

```bash
kill -STOP PID
```

Exemplo:

```bash
kill -STOP 2450
```

### Continuar processo pausado

```bash
kill -CONT PID
```

Exemplo:

```bash
kill -CONT 2450
```

---

## 8. Primeiro plano e segundo plano

### Executar comando normalmente

```bash
python script.py
```

O terminal fica ocupado até o processo terminar.

### Executar em segundo plano

```bash
python script.py &
```

O `&` executa o comando em segundo plano e libera o terminal.

### Ver processos em segundo plano do terminal atual

```bash
jobs
```

### Trazer processo para primeiro plano

```bash
fg
```

Se houver mais de um processo:

```bash
fg %1
```

### Enviar processo para segundo plano

Durante a execução de um comando, pressione:

```bash
Ctrl + Z
```

Isso pausa o processo. Depois execute:

```bash
bg
```

---

## 9. Manter processo rodando após fechar o terminal

### Usando `nohup`

```bash
nohup comando &
```

Exemplo:

```bash
nohup python script.py &
```

A saída normalmente é gravada em:

```bash
nohup.out
```

### Salvar saída em arquivo específico

```bash
nohup python script.py > saida.log 2>&1 &
```

---

## 10. Ver consumo de recursos

### Ver uso de CPU e memória

```bash
top
```

ou:

```bash
htop
```

### Ver memória RAM

```bash
free -h
```

### Ver uso de disco

```bash
df -h
```

### Ver tamanho de diretórios

```bash
du -sh *
```

---

## 11. Ver árvore de processos

```bash
pstree
```

Instalar no Ubuntu/Debian:

```bash
sudo apt install psmisc
```

Mostrar PIDs:

```bash
pstree -p
```

---

## 12. Ver processos de um usuário específico

```bash
ps -u nome_usuario
```

Exemplo:

```bash
ps -u douglas
```

Com mais detalhes:

```bash
ps aux | grep douglas
```

---

## 13. Ver processos usando uma porta

### Usando `ss`

```bash
sudo ss -tulnp
```

Filtrar por porta:

```bash
sudo ss -tulnp | grep 80
```

### Usando `lsof`

```bash
sudo lsof -i :80
```

Exemplo:

```bash
sudo lsof -i :443
```

---

## 14. Encerrar processo que usa uma porta

### Descobrir o processo

```bash
sudo lsof -i :8000
```

Exemplo de saída:

```bash
COMMAND  PID USER
python  2450 douglas
```

### Encerrar normalmente

```bash
kill 2450
```

### Forçar encerramento

```bash
kill -9 2450
```

---

## 15. Alterar prioridade de processos

No Linux, a prioridade é controlada pelo valor **nice**.

Quanto menor o valor, maior a prioridade.

| Nice | Prioridade |
|---|---|
| `-20` | Prioridade máxima |
| `0` | Prioridade padrão |
| `19` | Prioridade baixa |

### Iniciar processo com prioridade menor

```bash
nice -n 10 comando
```

Exemplo:

```bash
nice -n 10 python script.py
```

### Alterar prioridade de processo em execução

```bash
renice 10 -p PID
```

Exemplo:

```bash
renice 10 -p 2450
```

Para aumentar prioridade, geralmente é necessário usar `sudo`:

```bash
sudo renice -5 -p 2450
```

---

## 16. Gerenciar serviços com `systemctl`

Muitos processos são serviços do sistema, como `nginx`, `docker`, `postgresql`, `ssh` e outros.

### Ver status de um serviço

```bash
sudo systemctl status nome_servico
```

Exemplo:

```bash
sudo systemctl status nginx
```

### Iniciar serviço

```bash
sudo systemctl start nome_servico
```

### Parar serviço

```bash
sudo systemctl stop nome_servico
```

### Reiniciar serviço

```bash
sudo systemctl restart nome_servico
```

### Recarregar configuração sem reiniciar totalmente

```bash
sudo systemctl reload nome_servico
```

Exemplo:

```bash
sudo systemctl reload nginx
```

### Habilitar serviço no boot

```bash
sudo systemctl enable nome_servico
```

### Desabilitar serviço no boot

```bash
sudo systemctl disable nome_servico
```

---

## 17. Ver logs de processos e serviços

### Ver logs de um serviço

```bash
journalctl -u nome_servico
```

Exemplo:

```bash
journalctl -u nginx
```

### Ver logs em tempo real

```bash
journalctl -u nome_servico -f
```

Exemplo:

```bash
journalctl -u docker -f
```

### Ver logs desde hoje

```bash
journalctl -u nome_servico --since "today"
```

Exemplo:

```bash
journalctl -u nginx --since "today"
```

### Filtrar erros nos logs

```bash
journalctl -u nginx --since "today" | grep -Ei "error|failed|timeout|refused"
```

---

## 18. Comandos mais usados

| Comando | Função |
|---|---|
| `ps aux` | Lista todos os processos |
| `ps aux | grep nome` | Filtra processo pelo nome |
| `top` | Monitora processos em tempo real |
| `htop` | Monitora processos com interface melhor |
| `pidof nome` | Mostra PID de um processo |
| `pgrep nome` | Procura PID pelo nome |
| `pgrep -a nome` | Mostra PID e comando |
| `kill PID` | Encerra processo normalmente |
| `kill -9 PID` | Força encerramento |
| `pkill nome` | Encerra processo pelo nome |
| `killall nome` | Encerra todos os processos com o nome informado |
| `jobs` | Mostra processos em segundo plano no terminal atual |
| `fg` | Traz processo para primeiro plano |
| `bg` | Continua processo em segundo plano |
| `nohup comando &` | Mantém processo rodando após fechar terminal |
| `pstree -p` | Mostra árvore de processos com PID |
| `sudo ss -tulnp` | Mostra portas e processos |
| `sudo lsof -i :porta` | Mostra processo usando uma porta |
| `nice -n valor comando` | Inicia processo com prioridade definida |
| `renice valor -p PID` | Altera prioridade de processo existente |
| `systemctl status serviço` | Verifica status de serviço |
| `journalctl -u serviço -f` | Acompanha logs do serviço |

---

## 19. Exemplos práticos

### Encontrar e encerrar um processo Python

```bash
ps aux | grep python
```

Depois:

```bash
kill PID
```

Se necessário:

```bash
kill -9 PID
```

### Descobrir quem está usando a porta 8000

```bash
sudo lsof -i :8000
```

Depois:

```bash
kill PID
```

### Ver processos consumindo mais CPU

```bash
top
```

Dentro do `top`, pressione:

```bash
P
```

### Ver processos consumindo mais memória

```bash
top
```

Dentro do `top`, pressione:

```bash
M
```

### Rodar script em segundo plano e salvar log

```bash
nohup python script.py > script.log 2>&1 &
```

### Ver logs de um serviço em tempo real

```bash
journalctl -u nginx -f
```

---

## 20. Resumo rápido

```bash
ps aux
top
htop
pgrep nome
kill PID
kill -9 PID
pkill nome
jobs
fg
bg
nohup comando &
sudo lsof -i :porta
sudo systemctl status serviço
journalctl -u serviço -f
```

Esses comandos permitem visualizar processos, identificar consumo de recursos, encerrar programas travados, controlar execução em segundo plano, verificar portas em uso e acompanhar logs de serviços.
