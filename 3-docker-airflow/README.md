# 🛫 Day 5: Apache Airflow Setup with Docker Compose

## ✅ What I Did Today
- Installed **Apache Airflow** locally using **Docker Compose**.
- Launched Airflow services: Webserver, Scheduler, Worker, Database (PostgreSQL), Redis.
- Accessed the Airflow Web UI at `localhost:8080`.
- Created my **first DAG** that prints a simple "Hello, Data Engineer!" message.
- Learned about DAGs, tasks, and orchestration basics.

---

## 📚 What is Apache Airflow?
- **Apache Airflow** is a platform to **programmatically author, schedule, and monitor workflows**.
- Workflows are defined as **DAGs** (Directed Acyclic Graphs).
- Each node of a DAG represents a **task** (like running a bash command, Python function, SQL, etc.).
- Airflow is widely used in **Data Engineering**, **ETL**, and **ML Pipelines**.

---

## ⚙️ Setup Overview

### 📂 Project Structure

# Download airflow
```shell
curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.9.0/docker-compose.yaml'
```
# Set Required Environment Variables
```shell
echo -e "AIRFLOW_UID=$(id -u)" > .env
```
# Initialize the Database
```shell
docker-compose up airflow-init
```

# Bring Up Airflow

```shell
docker-compose up -d
```
# Containers will start:

- airflow-webserver

- airflow-scheduler

- airflow-worker

- postgres (Airflow metadata store)

- redis

# Access Airflow Web UI
Open:
👉 http://localhost:8080

Login default:

Username: airflow

Password: airflow

You will land on the Airflow Dashboard!

# Create Your First DAG
Inside your dags/ folder (under the airflow project folder), create a file:
hello_dag.py

```python
from airflow import DAG
from airflow.operators.bash import BashOperator
from datetime import datetime

default_args = {
    'start_date': datetime(2024, 1, 1),
}

with DAG(
    dag_id='hello_data_engineer',
    default_args=default_args,
    schedule_interval='@daily',  # run daily
    catchup=False,
) as dag:
    task1 = BashOperator(
        task_id='print_hello',
        bash_command='echo "Hello, Data Engineer!"'
    )
```
Now inside Airflow UI, you will see a DAG called hello_data_engineer.

Trigger it manually.

You should see logs showing Hello, Data Engineer!


