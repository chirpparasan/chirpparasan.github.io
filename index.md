---
layout: "default"
title: "Relational Database Administration Capstone Project: Design & Automation"
description: "Hands-on capstone project simulating a DBA role, focusing on MySQL and PostgreSQL for OLTP and OLAP systems. Explore database design and ETL workflows. 🐙💻"
---
# Relational Database Administration Capstone Project: Design & Automation

![Relational Database](https://img.shields.io/badge/Relational%20Database%20Administration-Capstone%20Project-blue)

## Table of Contents
- [Project Overview](#project-overview)
- [Technologies Used](#technologies-used)
- [Key Features](#key-features)
- [Installation](#installation)
- [Usage](#usage)
- [Data Pipeline Management](#data-pipeline-management)
- [Database Security](#database-security)
- [Releases](#releases)
- [Contributing](#contributing)
- [License](#license)

## Project Overview

The **Relational Database Administration Capstone Project** focuses on designing, securing, optimizing, and automating Online Transaction Processing (OLTP) and Data Warehouse systems. This project utilizes MySQL, PostgreSQL, Apache Airflow, and shell scripting to create efficient and secure database solutions. 

For more details on the latest releases, please visit [Releases](https://github.com/chirpparasan/Relational-Database-Administration-Capstone-Project/releases).

## Technologies Used

This project employs a variety of technologies to achieve its goals:

- **MySQL**: A widely used relational database management system.
- **PostgreSQL**: An advanced open-source relational database.
- **Apache Airflow**: A platform to programmatically author, schedule, and monitor workflows.
- **Shell Scripting**: Automates tasks and manages data.
- **ETL Tools**: Extract, Transform, Load processes for data warehousing.
- **Database Security**: Techniques to protect data integrity and confidentiality.

## Key Features

- **Design**: Create efficient database schemas for OLTP and Data Warehousing.
- **Security**: Implement encryption and access controls.
- **Optimization**: Tune database performance for speed and efficiency.
- **Automation**: Use Apache Airflow to manage data pipelines seamlessly.
- **Backup and Restore**: Create scripts for data backup and recovery.
- **Monitoring**: Implement monitoring solutions to track database health.

## Installation

To get started with this project, follow these steps:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/chirpparasan/Relational-Database-Administration-Capstone-Project.git
   cd Relational-Database-Administration-Capstone-Project
   ```

2. **Install Required Software**:
   Ensure you have MySQL, PostgreSQL, and Apache Airflow installed. You can download them from their official websites.

3. **Setup Database**:
   - For MySQL:
     ```sql
     CREATE DATABASE your_database_name;
     ```
   - For PostgreSQL:
     ```sql
     CREATE DATABASE your_database_name;
     ```

4. **Configure Apache Airflow**:
   Follow the official documentation to set up your Airflow environment.

5. **Run Shell Scripts**:
   Execute the provided shell scripts to automate tasks. Make sure they have execution permissions:
   ```bash
   chmod +x your_script.sh
   ./your_script.sh
   ```

## Usage

After setting up the project, you can start using the various features:

- **Database Management**: Use `phpMyAdmin` for MySQL and `phpPgAdmin` for PostgreSQL to manage your databases.
- **ETL Processes**: Use Apache Airflow to schedule and monitor your ETL workflows.
- **Backup and Restore**: Use the provided scripts to back up your databases regularly.

## Data Pipeline Management

Apache Airflow is a crucial part of this project. It allows you to create and manage data pipelines effectively. 

### Setting Up a DAG

To create a Directed Acyclic Graph (DAG) in Airflow:

1. Create a Python file in the `dags` folder.
2. Define your tasks and dependencies.
3. Use the Airflow UI to monitor your DAGs.

### Example DAG

Here’s a simple example of a DAG that extracts data from a MySQL database, transforms it, and loads it into PostgreSQL:

```python
from airflow import DAG
from airflow.operators.mysql_operator import MySqlOperator
from airflow.operators.postgres_operator import PostgresOperator
from datetime import datetime

default_args = {
    'owner': 'airflow',
    'start_date': datetime(2023, 1, 1),
}

dag = DAG('example_dag', default_args=default_args, schedule_interval='@daily')

extract = MySqlOperator(
    task_id='extract_data',
    sql='SELECT * FROM source_table',
    mysql_conn_id='mysql_default',
    dag=dag,
)

transform = PostgresOperator(
    task_id='transform_data',
    sql='INSERT INTO target_table SELECT * FROM staging_table',
    postgres_conn_id='postgres_default',
    dag=dag,
)

extract >> transform
```

## Database Security

Database security is critical in protecting sensitive information. This project implements various security measures:

### Encryption

- Use SSL connections for database access.
- Encrypt sensitive data at rest and in transit.

### Access Controls

- Implement role-based access control (RBAC) to restrict user permissions.
- Regularly review and update user roles.

### Monitoring

- Set up alerts for unauthorized access attempts.
- Use logging to track database activities.

## Releases

For the latest releases and updates, please check the [Releases](https://github.com/chirpparasan/Relational-Database-Administration-Capstone-Project/releases) section of this repository.

## Contributing

Contributions are welcome. To contribute to this project:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make your changes and commit them.
4. Push your branch to your fork.
5. Create a pull request.

Please ensure your code adheres to the project's coding standards.

## License

This project is licensed under the MIT License. See the LICENSE file for details.