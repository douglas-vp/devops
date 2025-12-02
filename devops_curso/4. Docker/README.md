# Docker: Labs Práticos e Guia de Comandos Essenciais

Este documento reúne em um único material um conjunto de **labs práticos de Docker** e um **guia de comandos essenciais**, permitindo tanto a prática guiada quanto a consulta rápida dos principais comandos utilizados no dia a dia de desenvolvimento e automação com containers.

---

## Parte I –Lab Docker: Do Básico ao Avançado

Este conjunto de labs práticos foi elaborado para ensinar o uso de Docker de forma eficiente no dia a dia de desenvolvimento e automação. O conteúdo inicia com comandos básicos e evolui para troubleshooting, cópia de arquivos, criação de imagens personalizadas e uso de `docker-compose`.

### 1. Pré-requisitos

- Docker instalado ([Instruções](https://docs.docker.com/get-docker/))
- Terminal Linux, WSL ou macOS

Verificar a versão instalada:

```bash
docker --version
```

Verificar se o serviço está ativo:

```bash
sudo systemctl status docker
```

---

### 2. Lab Docker

#### Objetivo geral

Executar comandos básicos do Docker garantindo a manutenção do acesso ao terminal remoto (por exemplo, via SSH) e evoluir para cenários mais avançados envolvendo aplicações em Python, FastAPI, Node.js, Docker Hub e Docker Compose.

---

### 3. Lab 1 – Comandos Básicos com Segurança Remota

#### 3.1 Baixar imagem do Nginx

```bash
docker pull nginx
```

#### 3.2 Rodar container em modo detached

```bash
docker run -d --name webserver -p 8080:80 nginx
```

#### 3.3 Verificar containers em execução

```bash
docker ps
```

#### 3.4 Verificar se o serviço está respondendo

```bash
curl http://localhost:8080
```

#### 3.5 Acessar o terminal do container

```bash
docker exec -it webserver bash
```

#### 3.6 Parar e remover o container

```bash
docker stop webserver
docker rm webserver
```

#### 3.7 Remover a imagem (opcional)

```bash
docker rmi nginx
```

---

### 4. Lab 2 – Docker com Python e FastAPI

#### 4.1 Criar estrutura do projeto

```bash
mkdir -p ~/labs/docker/fastapi-app
cd ~/labs/docker/fastapi-app
```

#### 4.2 Criar arquivos da aplicação

Criar o arquivo principal:

```bash
touch main.py
```

Conteúdo de `main.py`:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello from a Dockerized FastAPI app!"}
```

#### 4.3 Criar o arquivo `requirements.txt`

```bash
echo -e "fastapi
uvicorn" > requirements.txt
```

#### 4.4 Criar o Dockerfile

```Dockerfile
FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 8000

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

#### 4.5 Build da imagem

```bash
docker build -t fastapi-app .
```

#### 4.6 Executar o container

```bash
docker run -d -p 8000:8000 fastapi-app
```

#### 4.7 Testar e visualizar logs

Teste via `curl`:

```bash
curl http://localhost:8000/
```

Retorno esperado:

```json
{"message":"Hello from a Dockerized FastAPI app!"}
```

Visualizar logs:

```bash
docker logs $(docker ps -q --filter ancestor=fastapi-app)
```

#### 4.8 Parar e remover o container (opcional)

```bash
docker ps -q --filter ancestor=fastapi-app | xargs docker stop | xargs docker rm
```

---

### 5. Lab 3 – Docker Multistage com Node.js

#### 5.1 Criar estrutura do projeto

```bash
mkdir -p ~/labs/docker/app
cd ~/labs/docker/app
```

#### 5.2 Criar arquivos da aplicação

Criar diretório e arquivo principal:

```bash
mkdir -p src
touch src/index.js
```

Conteúdo de `src/index.js`:

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Hello from a professional Docker container!');
});

const PORT = process.env.PORT || 3000;
server.listen(PORT, () => {
  console.log(`Servidor rodando na porta ${PORT}`);
});
```

#### 5.3 Criar o arquivo `package.json`

```bash
touch package.json
```

Conteúdo sugerido de `package.json`:

```json
{
  "name": "docker-app",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  },
  "dependencies": {}
}
```

Estrutura de pastas esperada:

```bash
➜  tree
.
├── dockerfile
└── src
    ├── index.js
    └── package.json
```

#### 5.4 Criar Dockerfile otimizado (multistage)

```Dockerfile
# Etapa 1: build da aplicação (instalação de dependências)
FROM node:18 AS builder
WORKDIR /app
COPY src/package.json ./
RUN npm install
COPY src/ .

# Etapa 2: imagem final
FROM node:18-alpine
WORKDIR /app
COPY --from=builder /app .
EXPOSE 3000
CMD ["npm", "start"]
```

#### 5.5 Build da imagem

```bash
docker build -t devopsautomation:latest .
```

#### 5.6 Executar a imagem

```bash
docker run -d -p 3000:3000 devopsautomation:latest
```

#### 5.7 Validar e visualizar logs

Teste via `curl`:

```bash
curl http://localhost:3000
```

Retorno esperado:

```text
Hello from a professional Docker container!
```

Ver logs do container:

```bash
docker logs $(docker ps -q --filter ancestor=devopsautomation:latest)
```

Saída esperada (exemplo):

```text
Servidor rodando na porta 3000
```

#### 5.8 Parar e remover o container (opcional)

```bash
docker ps -q --filter ancestor=devopsautomation:latest | xargs docker stop | xargs docker rm
```

---

### 6. Lab 4 – Criando um `.gitignore` para Projetos Docker com Node.js

#### 6.1 Reutilizar o projeto existente

Reaproveitar o projeto criado no **Lab 3 – Docker Multistage com Node.js**. Navegar até o diretório base:

```bash
cd ~/labs
```

Inicializar o repositório na raiz (caso ainda não exista):

```bash
git init
```

#### 6.2 Criar o arquivo `.gitignore` na raiz do repositório

```bash
touch .gitignore
```

Conteúdo sugerido para `.gitignore`:

```gitignore
# Ignorar arquivos sensíveis e temporários dentro de docker/app
/docker/app/node_modules/
/docker/app/dist/
/docker/app/*.log
/docker/app/.env
/docker/app/.env*

# Pycache, logs e arquivos temporários em geral
**/__pycache__/
**/*.pyc
.DS_Store
*.tgz
```

#### 6.3 Testar o comportamento do `.gitignore`

Criação de arquivos simulando um ambiente real:

```bash
mkdir docker/app/node_modules
mkdir docker/app/dist
echo "segredo=abc" > docker/app/.env
```

Verificação com `git status`:

```bash
git status
```

As pastas e arquivos criados não devem aparecer como *Untracked files*.

#### 6.4 Adicionar e versionar apenas os arquivos necessários

```bash
git add .
git status
git commit -m "Configuração inicial com .gitignore para estrutura Docker/Node"
```

#### 6.5 Verificar arquivos ignorados

```bash
git check-ignore -v docker/app/.env docker/app/node_modules/
```

---

### 7. Lab 8 – Fazendo Push da Imagem Docker para o Docker Hub

#### 7.1 Pré-requisitos

- Conta ativa no [Docker Hub](https://hub.docker.com/).
- Login local com Docker CLI:

```bash
docker login
```

#### 7.2 Reutilizar a imagem do projeto

Utilizar a imagem criada no **Lab 3 – Docker Multistage com Node.js**.

Acessar a pasta do projeto:

```bash
cd ~/labs/docker/app
```

#### 7.3 Taguear a imagem com o nome do repositório remoto

Padrão:

```text
<usuario-dockerhub>/<nome-repositorio>:<tag>
```

Exemplo:

```bash
docker tag devopsautomation:latest iesodias/docker-node-app:1.0.0
```

#### 7.4 Fazer o push da imagem

```bash
docker push iesodias/docker-node-app:1.0.0
```

Opcionalmente:

```bash
docker tag devopsautomation:latest iesodias/docker-node-app:latest
docker push iesodias/docker-node-app:latest
```

#### 7.5 Verificar no Docker Hub

Acessar o repositório no Docker Hub e validar as tags publicadas.

#### 7.6 Baixar a imagem em outro ambiente

Em um host com Docker:

```bash
docker pull iesodias/docker-node-app:1.0.0
docker run -p 3000:3000 iesodias/docker-node-app:1.0.0
```

#### 7.7 Remover a imagem local

```bash
docker rmi iesodias/docker-node-app:1.0.0
```

---

### 8. Lab 9 – Orquestrando com Docker Compose

#### 8.1 Objetivo

Utilizar Docker Compose para subir uma aplicação Node.js juntamente com um banco PostgreSQL, simulando um ambiente completo de desenvolvimento.

#### 8.2 Estrutura do projeto

```text
docker-compose-lab/
├── docker-compose.yml
└── app/
    ├── dockerfile
    └── src/
        ├── index.js
        └── package.json
```

#### 8.3 Criar o `docker-compose.yml`

```yaml
version: '3.8'

services:
  node-app:
    build:
      context: ./app
      dockerfile: dockerfile
    ports:
      - "3000:3000"
    container_name: node_compose_app
    restart: unless-stopped
    depends_on:
      - db
    environment:
      - DATABASE_URL=postgres://devuser:devpass@db:5432/devdb

  db:
    image: postgres:15
    container_name: postgres_compose_db
    restart: unless-stopped
    ports:
      - "5432:5432"
    environment:
      POSTGRES_USER: devuser
      POSTGRES_PASSWORD: devpass
      POSTGRES_DB: devdb
    volumes:
      - pgdata:/var/lib/postgresql/data

volumes:
  pgdata:
```

#### 8.4 Subir a aplicação com Docker Compose

```bash
docker-compose up -d
```

#### 8.5 Validar funcionamento da aplicação

```bash
curl http://localhost:3000
```

Retorno esperado:

```text
Hello from a professional Docker container!
```

#### 8.6 Acessar o banco de dados

```bash
docker exec -it postgres_compose_db psql -U devuser -d devdb
```

Alguns comandos dentro do PostgreSQL:

```sql
\l  -- lista bancos
\dt -- lista tabelas
```

#### 8.7 Verificar status dos containers

```bash
docker-compose ps
```

#### 8.8 Ver logs da aplicação

```bash
docker-compose logs -f node-app
```

#### 8.9 Parar e remover os containers

```bash
docker-compose down -v
```

---

## Parte II – Guia de Comandos Essenciais do Docker para Desenvolvimento

Esta seção apresenta os principais comandos Docker que todo desenvolvedor deve conhecer para uso no dia a dia, incluindo gerenciamento de imagens, containers, volumes, redes e Docker Compose.

### 1. Comandos de verificação e ajuda

```bash
docker --version       # Exibe a versão instalada do Docker
docker info            # Mostra informações gerais do daemon, imagens e containers
docker help            # Exibe ajuda geral do Docker
docker <comando> --help  # Exibe ajuda específica para um comando
```

---

### 2. Gerenciamento de imagens

#### 2.1 Listar, baixar e remover imagens

```bash
docker images              # Lista as imagens disponíveis localmente
docker pull nginx          # Baixa a imagem 'nginx' do Docker Hub
docker rmi nginx           # Remove a imagem 'nginx'
docker rmi <id_imagem>     # Remove uma imagem pelo ID
```

#### 2.2 Construção de imagens

```bash
docker build -t minha-app:latest .   # Executa o build a partir de um Dockerfile no diretório atual
```

Parâmetros importantes:

- `-t nome:tag` → define o nome e a tag da imagem.
- `.` → indica o diretório atual como contexto de build.

---

### 3. Ciclo de vida de containers

#### 3.1 Criação e execução de containers

```bash
docker run nginx                          # Executa o container em foreground
docker run -d --name web -p 8080:80 nginx # Executa em modo detached, com nome e mapeamento de porta
docker run --rm -it ubuntu bash           # Executa container temporário em modo interativo com shell bash
```

Principais flags do `docker run`:

- `-d` → executa o container em background (detached).
- `--name` → atribui um nome ao container.
- `-p HOST:CONTAINER` → mapeia portas do host para o container (ex.: `8080:80`).
- `-v host_dir:container_dir` → monta um volume (ex.: `-v $(pwd):/app`).
- `-e VAR=valor` → define variáveis de ambiente.
- `--rm` → remove o container automaticamente ao finalizar.
- `-it` → habilita modo interativo com terminal.

#### 3.2 Listagem de containers

```bash
docker ps                # Lista apenas os containers em execução
docker ps -a             # Lista todos os containers, incluindo os parados
```

#### 3.3 Parar, iniciar e remover containers

```bash
docker stop web                     # Para o container 'web'
docker start web                    # Inicia novamente o container 'web'
docker restart web                  # Reinicia o container 'web'
docker rm web                       # Remove um container parado
docker rm -f web                    # Força parada e remoção do container
docker rm $(docker ps -aq)          # Remove todos os containers parados
```

---

### 4. Execução de comandos e inspeção

#### 4.1 Execução de comandos dentro do container

```bash
docker exec -it web bash      # Abre um shell bash dentro do container 'web'
docker exec -it web sh        # Abre um shell sh (imagens minimalistas como alpine)
docker exec web ls /usr/share/nginx/html  # Executa 'ls' em um diretório específico
```

#### 4.2 Inspeção de containers e imagens

```bash
docker inspect web      # Exibe informações detalhadas (JSON) sobre o container 'web'
docker inspect nginx    # Exibe informações detalhadas (JSON) sobre a imagem 'nginx'
```

---

### 5. Cópia de arquivos entre host e container

```bash
docker cp arquivo.txt web:/tmp/           # Copia arquivo do host para o container
docker cp web:/etc/nginx/nginx.conf .     # Copia arquivo do container para o host
```

---

### 6. Logs e troubleshooting

```bash
docker logs web                # Exibe os logs do container 'web'
docker logs -f web             # Exibe logs em tempo real (follow)
docker logs --tail 100 web     # Exibe apenas as últimas 100 linhas de log
```

Uso comum em conjunto:

```bash
docker ps
docker logs -f <nome_ou_id_container>
```

---

### 7. Volumes e redes (gestão básica)

#### 7.1 Volumes

```bash
docker volume ls               # Lista volumes disponíveis
docker volume create dados     # Cria um volume chamado 'dados'
docker volume rm dados         # Remove o volume 'dados'
```

Exemplo de uso:

```bash
docker run -d --name db -v dados:/var/lib/postgresql/data postgres
```

#### 7.2 Redes

```bash
docker network ls                      # Lista redes existentes
docker network create minha-net        # Cria uma rede do tipo bridge
docker network rm minha-net            # Remove a rede 'minha-net'
```

Exemplo de uso em containers conectados à mesma rede:

```bash
docker run -d --name db --network minha-net postgres
docker run -d --name api --network minha-net minha-api
```

---

### 8. Docker Compose

A partir das versões mais recentes, recomenda-se o uso de `docker compose` (com espaço) em vez de `docker-compose`.

#### 8.1 Comandos principais

No diretório onde está o arquivo `docker-compose.yml`:

```bash
docker compose up           # Sobe todos os serviços em foreground
docker compose up -d        # Sobe todos os serviços em background (detached)
docker compose down         # Derruba todos os serviços, containers e rede criada
docker compose ps           # Lista os serviços gerenciados pelo compose
docker compose logs         # Exibe logs de todos os serviços
docker compose logs -f api  # Exibe logs em tempo real apenas do serviço 'api'
```

---

### 9. Conjunto mínimo de comandos essenciais

A relação a seguir reúne um conjunto enxuto de comandos que cobre a maioria das necessidades cotidianas em desenvolvimento com Docker:

```bash
docker pull <imagem>                        # Baixar imagem do registry
docker images                               # Listar imagens locais
docker run -d --name <nome> -p HOST:PORTA <imagem>   # Rodar container em background com porta mapeada
docker ps                                   # Listar containers em execução
docker stop <container>                     # Parar um container
docker rm <container>                       # Remover um container
docker logs -f <container>                  # Acompanhar logs em tempo real
docker exec -it <container> bash            # Acessar shell dentro do container
docker build -t <nome>:tag .                # Construir uma imagem a partir de um Dockerfile
docker compose up -d && docker compose down # Subir e derrubar stack via Docker Compose
```

---

### 10. Considerações finais

O conjunto de labs apresentado na Parte I, combinado com o guia de comandos da Parte II, fornece uma base prática e conceitual sólida para o uso de Docker em ambientes de desenvolvimento. A prática contínua dos exercícios e o uso recorrente dos comandos essenciais contribuem para um fluxo de trabalho mais ágil, melhor troubleshooting e preparação para cenários mais avançados, como pipelines de CI/CD e orquestração em produção.
