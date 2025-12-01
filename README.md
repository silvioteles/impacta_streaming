# Impacta Streaming – Aula Prática Kafka (Data Integration)

Curso: MBA em Data Engineering
Professor: André Ricardo  
Disciplina: Integrated Data Platforms  
Aluno: Silvio Cezar da Silva Teles  
RA: 2502503

---

Este repositório contém o projeto da **aula prática de Data Integration com Apache Kafka**, utilizando Docker, JupyterLab e Kafka UI para simular um cenário de **streaming de dados de uma “rede social”**.

O objetivo é demonstrar, de ponta a ponta:

- Geração de eventos (producer)
- Ingestão e transporte via Kafka (cluster com 2 brokers)
- Consumo dos eventos (consumer)
- Persistência dos dados em arquivos CSV para análise posterior

---

## Arquitetura da Solução

A arquitetura é executada via **Docker Compose** e contempla:

- **Zookeeper** – Coordenação do cluster Kafka
- **Kafka 1 e Kafka 2** – Dois brokers para simular ambiente com mais de um servidor
- **Kafka UI** – Interface web para inspecionar tópicos, partições e mensagens
- **JupyterLab** – Ambiente para executar os notebooks de producer e consumer

**Fluxo resumido:**

1. `producer.ipynb` gera mensagens simulando eventos de usuários em uma rede social.
2. As mensagens são publicadas em um tópico Kafka.
3. `consumer.ipynb` consome as mensagens do tópico.
4. As mensagens consumidas são gravadas periodicamente em arquivos CSV na pasta `data`.

---

## Estrutura de Pastas

```text
impacta_streaming/
 ─ docker-compose.yml
 ─ notebooks/
    ─ producer.ipynb
    ─ consumer.ipynb
    ─ run_jupyterlab.sh
    ─ requirements.txt
 ─ data/                # Arquivos CSV gerados pelo consumer
 ─ imagens/             # Evidências de execução (prints telas aplicação)
```

As evidências de execução estão disponíveis na pasta `impacta_streaming/notebooks/imagens`.

---

## Como Executar

1. **Clone o repositório:**

   git clone https://github.com/seu-usuario/impacta_streaming.git
   cd impacta_streaming

2. **Suba o ambiente Docker:**

   docker-compose up -d

3. **Instale as dependências Python:**

   pip install -r notebooks/requirements.txt

4. **Acesse o JupyterLab:**

   O JupyterLab estará disponível em `http://localhost:8888` (verifique o token no log do container ou use o script `run_jupyterlab.sh`).
5. **Execute os notebooks:**

   `producer.ipynb`: Gera e envia eventos para o Kafka.

   `consumer.ipynb`: Consome eventos do Kafka e salva em CSV na pasta `data`.
6. **Acesse o Kafka UI:**

   Interface web disponível em `http://localhost:8080` para monitorar tópicos e mensagens.

---

## Requisitos
- Docker e Docker Compose
- Python 3.8+
- Navegador web para acessar JupyterLab e Kafka UI

---

## Licença
Uso acadêmico.
