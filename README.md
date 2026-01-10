# API Product – Node.js + Python with Docker

This project demonstrates an architecture based on **microservices**, using **Docker** and **Docker Compose**, where a **Python API** is responsible for the product CRUD and a **Node.js API** consumes the Python API to list the registered data.

---

## 📌 About

The project is composed of two main services:

### 🔹 Python API
- Implements a **product CRUD** with MySQL
- Uses **Redis** to cache data on read endpoints
- Exposes REST routes with Flask

When the cache is available, the response is returned avoiding database queries.
If the cache is not available, the data is fetched from the database and returned to the application.

---

### 🔹 Node.js API
- Acts as a **consumer API**
- Performs HTTP requests to the Python API
- Displays the data registered in the base API
- Implemented with **Express** and **Axios**

The entire environment runs in Docker containers, with each service having its own **Dockerfile**.

---

## Features

### 📋 Functional Requirements (FR)
- FR01: Allow registering products with description, category, and price
- FR02: Allow listing all registered products
- FR03: Allow updating existing products
- FR04: Allow removing products by identifier
- FR05: Allow access to products via the consumer API (Node.js)

---

### ⚙️ Non-Functional Requirements (NFR)
- NFR01: Use Redis as cache for read operations
- NFR02: Ensure automatic cache invalidation on write operations
- NFR03: Persist data in a MySQL database
- NFR04: Use Docker for service isolation

---

## ▶️ Run

### 1️⃣ Clone the repository
```
git clone https://github.com/GuilhermeOliveiraAgenor/docker-network-apis.git
cd docker-network-apis
```

### 2️⃣ Run the deploy script

The script starts the containers, runs tests, and displays logs
```
chmod +x deploy.sh
./deploy.sh
```

(Alternative deploy) - To start only the services
```
docker compose build
docker compose up -d
```
