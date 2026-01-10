# API Product – Node.js + Python com Docker

Este projeto demonstra uma arquitetura baseada em **microserviços**, utilizando **Docker** e **Docker Compose**, onde uma **API em Python** é responsável pelo CRUD de produtos e uma **API em Node.js** consome a API Python para listar os dados cadastrados.

---

## 📌 About

O projeto é composto por dois serviços principais:

### 🔹 API Python
- Implementa um **CRUD de produtos** com Mysql
- Utiliza **Redis** para cache dos dados nos endpoints de leitura
- Expõe rotas REST com Flask

Quando o cache está disponível, a resposta é retornada evitando consultas ao banco de dados.  
Na ausência de cache, os dados são buscados no banco e são retornadas para a aplicação.

---

### 🔹 API Node.js
- Atua como **API consumidora**
- Realiza requisições HTTP para a API Python
- Exibe os dados cadastrados na API base
- Implementada com **Express** e **Axios**

Todo o ambiente é executado em containers Docker com cada serviço possuindo seu próprio **Dockerfile**.

---

## Features

### 📋 Requisitos Funcionais (RF)
- RF01: Permitir cadastrar produtos com descrição, categoria e preço
- RF02: Permitir listar todos os produtos cadastrados
- RF03: Permitir atualizar produtos existentes
- RF04: Permitir remover produtos pelo identificador
- RF05: Permitir acesso aos produtos via API consumidora (Node.js)

---

### ⚙️ Requisitos Não Funcionais (RNF)
- RNF01: Utilizar Redis como cache para operações de leitura
- RNF02: Garantir invalidação automática do cache em operações de escrita
- RNF03: Persistir os dados em banco MySQL
- RNF04: Utilizar Docker para isolamento dos serviços

---

## ▶️ Run

### 1️⃣ Clonar o repositório

```
git clone https://github.com/GuilhermeOliveiraAgenor/docker-network-apis.git
cd docker-network-apis
```

### 2️⃣ Execute o arquivo de deploy

-  O arquivo sobe os containers, executa testes e exibe os logs
```
chmod +x deploy.sh
./deploy.sh
```

##

(Deploy alternativo) - Para subir apenas os serviços
```
docker compose build
docker compose up -d
```


