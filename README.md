# **Kong and Konga - API gateway**

Este projeto utiliza Docker Compose para configurar um ambiente com os seguintes serviços:

- **PostgreSQL:** Banco de dados para o Kong e o Konga.
- **Kong:** API Gateway para gerenciar APIs e microserviços.
- **Konga:** Interface gráfica para administração do Kong.

## **Pré-requisitos**

- [Docker](https://www.docker.com/products/docker-desktop) instalado.
- [Docker Compose](https://docs.docker.com/compose/install/) instalado.

> **Nota**
> Certifique-se de que as portas `5432`, `8000`, `8001`, `8443`, `8444` e `1337` estejam livres em sua máquina antes de iniciar os containers.

## **Estrutura do Projeto**

O projeto é composto pelos seguintes arquivos:

- `docker-compose.yml`: Define os serviços do Docker Compose.
- `.env`: Contém as variáveis de ambiente utilizadas no `docker-compose.yml`.
- `README.md`: Este arquivo com instruções de uso.

## **Configuração**

### **1. Clonar o Repositório**

Clone este repositório para a sua máquina local:

```env
git clone https://github.com/seu-usuario/seu-repo-kong-konga.git
cd seu-repo-kong-konga
```

### **2. Criar o Arquivo `.env`**

Crie um arquivo chamado `.env` na raiz do projeto com o seguinte conteúdo:

```env
# PostgreSQL
POSTGRES_USER=kong
POSTGRES_PASSWORD=kong
POSTGRES_DB=kong

# Kong
KONG_DATABASE=postgres
KONG_PG_HOST=kong-database
KONG_PG_USER=kong
KONG_PG_PASSWORD=kong
KONG_PG_DATABASE=kong

# Konga
KONGA_PORT=1337
KONGA_DB_ADAPTER=postgres
KONGA_DB_URI=postgresql://kong:kong@kong-database:5432/kong?currentSchema=kong
KONGA_NODE_ENV=dev
KONGA_LOG_LEVEL=debug
KONGA_HOST=0.0.0.0
```

### **3. Subir os Containers**

Execute o seguinte comando para iniciar os serviços:

```env
docker-compose up -d
```

Este comando irá:

- Iniciar o banco de dados PostgreSQL.
- Executar as migrações do Kong.
- Iniciar o Kong e o Konga.

### **4. Acessar os Serviços**

Após os containers estarem em execução, você pode acessar:

- **Konga (Interface Gráfica):** http://localhost:1337
- **Kong Admin API:** http://localhost:8001
- **Kong Proxy:** http://localhost:8000