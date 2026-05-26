# AI-Powered SQL Query Generator

## Project Overview

This project is an AI-powered SQL Query Generator that converts natural language prompts into optimized SQL queries using OpenAI GPT models.

Instead of manually writing complex SQL queries, users can enter plain English requests such as:

```text
"Show all users older than 30"
```

The system automatically:

- Generates optimized SQL queries
- Validates SQL syntax
- Executes queries on MySQL
- Returns results
- Provides optimization suggestions

The project includes:

- FastAPI backend
- Streamlit frontend
- OpenAI-powered query generation
- MySQL database integration
- Query optimization and validation

---

# Features

- Natural language to SQL conversion
- AI-generated optimized SQL queries
- MySQL database connectivity
- SQL syntax validation
- Query execution engine
- SQL optimization suggestions
- Interactive Streamlit UI
- FastAPI backend APIs
- Environment-based configuration

---

# Tech Stack

- Python
- FastAPI
- Streamlit
- OpenAI API
- LangChain
- SQLAlchemy
- MySQL
- sqlparse
- Pydantic

---

# Project Architecture

```text
          ┌─────────────────────┐
          │ Natural Language UI │
          │    (Streamlit)      │
          └──────────┬──────────┘
                     │
                     ▼
          ┌─────────────────────┐
          │   FastAPI Backend   │
          │      app.py         │
          └──────────┬──────────┘
                     │
                     ▼
          ┌─────────────────────┐
          │ Query Generator AI  │
          │ query_generator.py  │
          └──────────┬──────────┘
                     │
         ┌───────────┴───────────┐
         ▼                       ▼
 ┌───────────────┐      ┌────────────────┐
 │ SQL Validator │      │ Query Optimizer│
 │   sqlparse    │      │ EXPLAIN PLAN   │
 └───────────────┘      └────────────────┘
                     │
                     ▼
             ┌─────────────┐
             │   MySQL DB  │
             └─────────────┘
```

---

# Folder Structure

```text
project/
│
├── app.py
├── ui.py
├── database.py
├── query_generator.py
├── requirements.txt
├── .env
│
└── README.md
```

---

# Installation

## 1. Clone Repository

```bash
git clone <repository_url>
cd project
```

---

## 2. Create Environment

### Using Conda

```bash
conda create --name ai_sql_env python=3.10
```

Activate environment:

```bash
conda activate ai_sql_env
```

---

# 3. Install Dependencies

```bash
pip install -r requirements.txt
```

If any package is missing:

```bash
pip install sqlparse
pip install streamlit
```

---

# requirements.txt

```txt
langchain
llama-index
crewai
chromadb

openai
transformers
sentence-transformers

fastapi
uvicorn
pydantic

sqlalchemy
psycopg2-binary
pyodbc
mysql-connector-python
snowflake-connector-python

tqdm
python-dotenv
loguru

pytest

sqlparse
streamlit
```

---

# Environment Variables

Create a `.env` file:

```env
MYSQL_HOST=localhost
MYSQL_USERNAME=root
MYSQL_PASSWORD=root
MYSQL_DATABASE=test_db
MYSQL_PORT=3306

OPENAI_API_KEY=your_openai_api_key
```

---

# MySQL Setup

Install:

- MySQL Community Server
- MySQL Workbench

Create database:

```sql
CREATE DATABASE test_db;
```

Create sample table:

```sql
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    age INT,
    city VARCHAR(100)
);
```

Insert sample data:

```sql
INSERT INTO users(name, age, city)
VALUES
('John', 35, 'Toronto'),
('Alice', 28, 'New York'),
('Bob', 40, 'Chicago');
```

---

# File Explanations

## `database.py`

Responsible for:

- Database connection
- Schema retrieval
- Connection testing

### Functions

```python
test_connection()
get_schema()
```

---

## `query_generator.py`

Core AI logic for SQL generation.

### Responsibilities

- Generate SQL queries using OpenAI
- Clean AI output
- Validate SQL syntax
- Execute SQL queries
- Generate optimization suggestions

### Functions

```python
clean_sql_output()
validate_sql_query()
generate_sql()
suggest_indexes()
execute_query()
```

---

## `app.py`

FastAPI backend server.

### API Routes

| Endpoint | Purpose |
|---|---|
| `/generate-sql` | Generate SQL from natural language |
| `/execute-sql` | Execute SQL query |

---

## `ui.py`

Streamlit frontend application.

### Features

- Natural language input
- SQL query generation
- Query execution
- Result visualization
- Optimization suggestions

---

# Running the Project

---

## Step 1: Start FastAPI Backend

```bash
uvicorn app:app --reload
```

Backend runs on:

```text
http://127.0.0.1:8000/docs
```

---

## Step 2: Start Streamlit Frontend

```bash
streamlit run ui.py
```

Frontend runs on:

```text
http://localhost:8501
```

---

# Usage Example

## User Input

```text
Show users older than 30
```

---

## AI Generated SQL

```sql
SELECT * FROM users
WHERE age > 30;
```

---

## Query Result

```json
[
  {
    "id": 1,
    "name": "John",
    "age": 35,
    "city": "Toronto"
  },
  {
    "id": 3,
    "name": "Bob",
    "age": 40,
    "city": "Chicago"
  }
]
```

---

# API Workflow

```text
User Prompt
     ↓
Streamlit UI
     ↓
FastAPI Backend
     ↓
OpenAI GPT Model
     ↓
SQL Query Generation
     ↓
SQL Validation
     ↓
MySQL Execution
     ↓
Results + Optimization Suggestions
```

---

# Query Optimization

The system uses:

- SQL validation
- EXPLAIN execution plans
- Index recommendations
- Query performance analysis

Example optimization:

```text
Consider adding an index on frequently filtered columns.
```

---

# Common Errors

## Missing OpenAI Key

```text
OPENAI_API_KEY missing
```

### Solution

Add correct API key inside `.env`.

---

## MySQL Connection Error

```text
Access denied for user
```

### Solution

Verify:

- MySQL username
- Password
- Database name
- Port number

---

## Missing Package Error

```text
ModuleNotFoundError
```

### Solution

```bash
pip install <package_name>
```

---

# Future Improvements

- Multi-database support
- PostgreSQL integration
- Snowflake integration
- Query caching
- Authentication system
- Query history
- Role-based access
- SQL visualization
- AI-powered schema understanding
- Query explanation generation

---

# Conclusion

This project demonstrates how AI can simplify database interactions by converting natural language into executable SQL queries.

It combines:

- OpenAI-powered query generation
- FastAPI backend APIs
- Streamlit UI
- SQL validation
- Query optimization
- MySQL integration

to create an intelligent AI-assisted SQL querying platform.
