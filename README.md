# Order Management System

Este projeto é composto por diversos microsserviços que, juntos, formam um sistema de gerenciamento de pedidos. Cada microsserviço é responsável por uma parte específica do sistema, como gerenciamento de clientes, produtos, pagamentos, estoque e pedidos. A comunicação entre os serviços é feita por meio de APIs REST e Kafka.

## Pré-requisitos

Antes de executar o projeto, certifique-se de que você possui os seguintes itens instalados em sua máquina:

- **Docker**: Para executar os containers.
- **Docker Compose**: Para orquestrar os serviços.

## Como executar o projeto

1. **Clone o repositório**:
   ```bash
   git clone <URL_DO_REPOSITORIO>
   cd <NOME_DO_REPOSITORIO>
   ```

2. **Certifique-se de que as portas necessárias estão livres**:
    - Banco de dados: `5433`, `5434`, `5435`, `5436`, `5437`
    - Microsserviços: `8080`, `8081`, `8082`, `8083`, `8084`, `8085`
    - Kafka e Zookeeper: `2181`, `29092`, `9092`

3. **Suba os serviços com o Docker Compose**:
   Execute o seguinte comando na raiz do projeto:
   ```bash
   docker-compose up -d
   ```

4. **Verifique se os serviços estão rodando**:
   Use o comando abaixo para verificar o status dos containers:
   ```bash
   docker ps
   ```

5. **Acesse os microsserviços**:
    - **Receiver**: `http://localhost:8080`
    - **Product**: `http://localhost:8081`
    - **Client**: `http://localhost:8082`
    - **Payment**: `http://localhost:8083`
    - **Order**: `http://localhost:8084`
    - **Inventory**: `http://localhost:8085`

## Estrutura do Projeto

O projeto é composto pelos seguintes serviços:

- **Receiver**: Responsável por receber requisições externas e encaminhá-las para os serviços internos.
- **Product**: Gerencia informações sobre produtos.
- **Client**: Gerencia informações sobre clientes.
- **Payment**: Processa pagamentos.
- **Order**: Gerencia pedidos e integra os outros serviços.
- **Inventory**: Gerencia o estoque de produtos.

Além disso, o projeto utiliza:

- **PostgreSQL**: Banco de dados para cada microsserviço.
- **Kafka**: Para comunicação assíncrona entre os serviços.
- **Zookeeper**: Necessário para o Kafka.

## Encerrando os serviços

Para parar e remover os containers, execute:
```bash
docker-compose down
```

## Observações

- Certifique-se de que as imagens Docker necessárias estão disponíveis no Docker Hub ou no repositório especificado no `docker-compose.yml`.
- Caso algum serviço não inicie corretamente, verifique os logs com:
  ```bash
  docker logs <NOME_DO_CONTAINER>
  ```