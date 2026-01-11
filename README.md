# 🚀 Projeto Docker – Microsserviços PHP, Nginx e MySQL
![Docker CI](https://github.com/alexpaulo100/toshiro-shibakita/actions/workflows/docker-ci.yml/badge.svg)


Este repositório apresenta uma **arquitetura de microsserviços containerizada com Docker**, baseada em boas práticas amplamente utilizadas no mercado. O projeto demonstra a separação clara entre **camada de aplicação (PHP)**, **servidor web (Nginx)** e **banco de dados (MySQL)**, garantindo independência entre aplicações e infraestrutura.

O projeto foi inspirado no desafio proposto por **Denilson Bonatti (DIO)**, porém evoluído com melhorias arquiteturais, organização de diretórios e padronização de configuração via variáveis de ambiente.

---

## 🧱 Arquitetura da Solução

A aplicação é composta por três serviços principais:

* **Nginx** – Responsável por servir as requisições HTTP e atuar como reverse proxy
* **PHP (FPM)** – Camada de aplicação responsável pela lógica de negócio
* **MySQL** – Banco de dados relacional

Todos os serviços se comunicam através de uma **rede Docker bridge dedicada**.

```
┌──────────┐     ┌──────────┐     ┌──────────┐
│  Nginx   │ ─▶  │   PHP    │ ─▶  │  MySQL   │
└──────────┘     └──────────┘     └──────────┘
```

---

## 📂 Estrutura de Diretórios

```
.
├── app/                # Aplicação PHP
│   ├── Dockerfile
│   └── index.php
│
├── nginx/              # Configuração do Nginx
│   ├── Dockerfile
│   └── nginx.conf
│
├── db/                 # Inicialização do banco
│   └── init.sql
│
├── .gitignore
├── .env.example        # Exemplo de variáveis de ambiente
├── docker-compose.yml  # Orquestração dos containers
└── README.md
```

---

## ⚙️ Tecnologias Utilizadas

* Docker & Docker Compose
* PHP 8.2 (PHP-FPM-bullseye)
* Nginx
* MySQL 8.0
* Linux

---

## 🔐 Configuração por Variáveis de Ambiente

A aplicação segue o padrão **12-Factor App**, utilizando variáveis de ambiente para configuração:

Exemplo (`.env.example`):

```
DB_HOST=database
DB_NAME=app_db
DB_USER=app_user
DB_PASSWORD=app_pass
```

⚠️ O arquivo `.env` **não deve ser versionado**.

---

## ▶️ Como Executar o Projeto

### 1️⃣ Clonar o repositório

```
git clone https://github.com/alexpaulo100/toshiro-shibakita.git
cd toshiro-shibakita
```

### 2️⃣ Criar o arquivo de ambiente

```
cp .env.example .env
```

### 3️⃣ Subir os containers

```
docker compose up -d --build
```

### 4️⃣ Acessar a aplicação

```
http://localhost:8080
```

---

## 🧪 Funcionamento da Aplicação

A cada acesso à aplicação:

* Uma conexão com o MySQL é realizada
* Um registro aleatório é inserido na tabela `dados`
* O hostname do container é gravado no banco

Isso demonstra, na prática, **balanceamento, rastreabilidade e comunicação entre containers**.

---

## 🧠 Desafios Técnicos Resolvidos

* Padronização de configuração via variáveis de ambiente
* Correção de erro de autenticação causado por variável incorreta (`DB_PASS` vs `DB_PASSWORD`)
* Instalação correta das extensões PHP (`mysqli`, `pdo_mysql`)
* Organização da arquitetura seguindo boas práticas de microsserviços

---

## 🚀 Próximas Evoluções

* CI/CD com GitHub Actions
* Healthcheck nos containers
* Hardening de segurança (usuários e permissões)
* Observabilidade (logs e métricas)

---

## 👨‍💻 Autor

**Alex Silva**
Engenheiro de Dados | Backend Developer
Apaixonado por dados, containers e arquitetura de sistemas.

---

📌 *Este projeto faz parte do meu portfólio técnico e demonstra minha capacidade de diagnosticar, implementar e evoluir soluções containerizadas em ambientes reais.*
