# Redirecionamentos e Busca com `grep`

## 18. Resumo dos redirecionamentos

| Comando | Função | Exemplo |
|---|---|---|
| `comando > saida.txt` | Salva a saída normal em um arquivo, sobrescrevendo o conteúdo anterior. | `ls -la > saida.txt` |
| `comando >> saida.txt` | Adiciona a saída normal ao final de um arquivo, sem apagar o conteúdo anterior. | `ls -la >> saida.txt` |
| `comando 2> erros.txt` | Salva somente os erros em um arquivo, sobrescrevendo o conteúdo anterior. | `ls /pasta/inexistente 2> erros.txt` |
| `comando 2>> erros.txt` | Adiciona somente os erros ao final de um arquivo. | `ls /pasta/inexistente 2>> erros.txt` |
| `comando > saida.txt 2> erros.txt` | Salva a saída normal em um arquivo e os erros em outro arquivo separado. | `find / -name "*.log" > saida.txt 2> erros.txt` |
| `comando > resultado.txt 2>&1` | Salva a saída normal e os erros no mesmo arquivo. | `find / -name "*.log" > resultado.txt 2>&1` |
| `comando >> resultado.txt 2>&1` | Adiciona a saída normal e os erros ao final do mesmo arquivo. | `find / -name "*.log" >> resultado.txt 2>&1` |
| `comando &> resultado.txt` | Salva a saída normal e os erros no mesmo arquivo. Forma curta suportada no Bash. | `find / -name "*.log" &> resultado.txt` |
| `comando 2> /dev/null` | Ignora somente os erros. | `find / -name "*.log" 2> /dev/null` |
| `comando > /dev/null` | Ignora somente a saída normal e mantém os erros no terminal. | `find / -name "*.log" > /dev/null` |
| `comando > /dev/null 2>&1` | Ignora a saída normal e os erros. | `find / -name "*.log" > /dev/null 2>&1` |

---

## 19. Resumo do `grep`

| Comando | Função | Exemplo |
|---|---|---|
| `grep "texto" arquivo.txt` | Procura um texto dentro de um arquivo. | `grep "erro" arquivo.log` |
| `grep -i "texto" arquivo.txt` | Procura um texto ignorando maiúsculas e minúsculas. | `grep -i "erro" arquivo.log` |
| `grep -n "texto" arquivo.txt` | Mostra o número da linha onde o texto foi encontrado. | `grep -n "erro" arquivo.log` |
| `grep -r "texto" pasta/` | Procura um texto de forma recursiva dentro de uma pasta. | `grep -r "erro" /var/log` |
| `grep -rin "texto" pasta/` | Busca recursivamente, ignora maiúsculas/minúsculas e mostra número da linha. | `grep -rin "erro" .` |
| `grep -v "texto" arquivo.txt` | Mostra as linhas que não contêm o texto pesquisado. | `grep -v "sucesso" arquivo.log` |
| `grep -w "texto" arquivo.txt` | Procura a palavra exata. | `grep -w "erro" arquivo.log` |
| `grep -c "texto" arquivo.txt` | Conta quantas linhas contêm o texto pesquisado. | `grep -c "erro" arquivo.log` |
| `grep -l "texto" *.log` | Mostra apenas os nomes dos arquivos que contêm o texto pesquisado. | `grep -l "erro" *.log` |
| `grep -E "texto1|texto2" arquivo.txt` | Procura múltiplos padrões usando expressão regular estendida. | `grep -E "erro|falha" arquivo.log` |
| `grep -Ei "texto1|texto2" arquivo.txt` | Procura múltiplos padrões ignorando maiúsculas e minúsculas. | `grep -Ei "erro|falha|error|failed" arquivo.log` |
| `grep -A 3 "texto" arquivo.txt` | Mostra a linha encontrada e 3 linhas depois. | `grep -A 3 "erro" arquivo.log` |
| `grep -B 3 "texto" arquivo.txt` | Mostra 3 linhas antes da linha encontrada. | `grep -B 3 "erro" arquivo.log` |
| `grep -C 3 "texto" arquivo.txt` | Mostra 3 linhas antes e 3 linhas depois da linha encontrada. | `grep -C 3 "erro" arquivo.log` |
| `grep --include="*.log" -r "texto" pasta/` | Busca recursivamente apenas em arquivos com determinada extensão. | `grep --include="*.log" -r "erro" /var/log` |
| `grep --exclude="*.zip" -r "texto" pasta/` | Ignora arquivos com determinada extensão durante a busca. | `grep --exclude="*.zip" -r "erro" .` |
| `grep --exclude-dir=".git" -r "texto" pasta/` | Ignora um diretório específico durante a busca. | `grep --exclude-dir=".git" -r "erro" .` |

---

## 20. Combinações de `grep` com redirecionamento

| Comando | Função | Exemplo |
|---|---|---|
| `grep "texto" arquivo > resultado.txt` | Salva o resultado da busca em um arquivo. | `grep "erro" app.log > resultado.txt` |
| `grep "texto" arquivo >> resultado.txt` | Adiciona o resultado da busca ao final de um arquivo. | `grep "erro" app.log >> resultado.txt` |
| `grep -n "texto" arquivo > resultado.txt` | Salva o resultado com número da linha. | `grep -n "erro" app.log > erros_com_linha.txt` |
| `grep -r "texto" pasta > resultado.txt` | Salva o resultado de uma busca recursiva. | `grep -r "erro" /var/log > resultado_logs.txt` |
| `grep -r "texto" pasta 2> erros.txt` | Salva somente os erros da execução do `grep`. | `grep -r "erro" /var/log 2> erros.txt` |
| `grep -r "texto" pasta > resultado.txt 2> erros.txt` | Salva os resultados encontrados e os erros em arquivos separados. | `grep -r "erro" /var/log > resultado.txt 2> erros.txt` |
| `grep -r "texto" pasta > resultado.txt 2>&1` | Salva os resultados encontrados e os erros no mesmo arquivo. | `grep -r "erro" /var/log > resultado_completo.txt 2>&1` |
| `grep -r "texto" pasta 2> /dev/null` | Executa a busca ocultando erros, como mensagens de permissão negada. | `grep -r "erro" /var/log 2> /dev/null` |
| `grep -rinEi "p1|p2|p3" . > relatorio.txt` | Gera um relatório de busca recursiva com múltiplos termos. | `grep -rinEi "error|erro|failed|falha|exception|timeout" . > relatorio_erros.txt` |
| `grep -rinEi "p1|p2|p3" . > relatorio.txt 2> erros_execucao.txt` | Gera um relatório de ocorrências e salva erros de execução separadamente. | `grep -rinEi "error|erro|failed|falha|exception|timeout" . > relatorio_erros.txt 2> erros_execucao.txt` |
| `grep -rinEi "p1|p2|p3" . > relatorio_completo.txt 2>&1` | Gera um relatório completo com resultados e erros no mesmo arquivo. | `grep -rinEi "error|erro|failed|falha|exception|timeout" . > relatorio_completo.txt 2>&1` |

---

## 21. Exemplos práticos

| Situação | Comando |
|---|---|
| Procurar erros em um arquivo de log. | `grep -i "error" app.log` |
| Procurar erros e salvar em `.txt`. | `grep -i "error" app.log > erros.txt` |
| Procurar erros com número da linha. | `grep -ni "error" app.log` |
| Procurar múltiplos termos de erro. | `grep -Ei "error|failed|exception|timeout" app.log` |
| Procurar múltiplos termos e salvar em arquivo. | `grep -Ei "error|failed|exception|timeout" app.log > erros.txt` |
| Buscar erros em todos os arquivos da pasta atual. | `grep -rinEi "error|erro|failed|falha|exception|timeout" .` |
| Buscar erros e ignorar mensagens de permissão. | `grep -rinEi "error|erro|failed|falha|exception|timeout" . 2> /dev/null` |
| Buscar erros e salvar resultados e erros separados. | `grep -rinEi "error|erro|failed|falha|exception|timeout" . > resultado.txt 2> erros_execucao.txt` |
| Buscar erros e salvar tudo em um único arquivo. | `grep -rinEi "error|erro|failed|falha|exception|timeout" . > resultado_completo.txt 2>&1` |
| Filtrar logs em tempo real. | `tail -f app.log | grep -i "error"` |
| Filtrar logs em tempo real e salvar. | `tail -f app.log | grep -i "error" > erros_tempo_real.txt` |
| Filtrar logs de serviço com `journalctl`. | `journalctl -u nginx --since "today" | grep -Ei "error|failed|timeout"` |
| Filtrar logs de container Docker. | `docker logs nome_container | grep -Ei "error|failed|exception"` |
| Filtrar logs de container em tempo real. | `docker logs -f nome_container | grep -Ei "error|failed|exception"` |

---

## 22. Comando recomendado para investigação de erros

```bash
grep -rinEi "error|erro|failed|falha|exception|timeout|refused" . > relatorio_erros.txt 2> erros_execucao.txt
```

## Explicação

| Parte | Função |
|---|---|
| `grep` | Comando usado para buscar texto. |
| `-r` | Busca recursivamente nas pastas. |
| `-i` | Ignora maiúsculas e minúsculas. |
| `-n` | Mostra o número da linha. |
| `-E` | Permite usar múltiplos padrões com `|`. |
| `"error|erro|failed|falha|exception|timeout|refused"` | Termos pesquisados. |
| `.` | Busca a partir da pasta atual. |
| `> relatorio_erros.txt` | Salva os resultados encontrados. |
| `2> erros_execucao.txt` | Salva erros de execução, como permissão negada. |
