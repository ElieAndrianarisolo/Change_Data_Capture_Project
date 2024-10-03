# Data Engineering Project - CDC with Debezium, Kafka, Postgres, and Docker

## Overview

This project demonstrates the implementation of Change Data Capture (CDC) using Debezium with Kafka and Postgres in a Dockerized environment. As part of a Data Engineering initiative, I have developed a Python script to simulate financial transactions and insert them into a PostgreSQL database. This environment allows for real-time monitoring and capturing of database changes, making it ideal for testing CDC pipelines.

The system architecture includes services such as Kafka, Zookeeper, and Postgres, with Debezium providing CDC functionality. The project aims to showcase how change data from a PostgreSQL database can be captured and streamed via Kafka using Debezium, enabling near real-time data replication.

## Prerequisites

Before running this project, ensure you have the following installed:

- Python 3.9+
- PostgreSQL server (local or remote)
- Docker and Docker Compose installed
- Basic knowledge of Docker, Kafka, and PostgreSQL
- Required Python Libraries: Install using the command:

```bash
pip install psycopg2-binary faker
```

### Docker Compose Services

The services in the `docker-compose.yml` file are designed to create a distributed system with multiple components working together. Below are the key services:

- **Zookeeper**: Centralized service for maintaining configuration and synchronization.
- **Kafka Broker**: Distributed streaming platform for handling real-time data feeds.
- **Confluent Control Center**: Web-based tool for managing and monitoring Kafka.
- **Debezium**: Distributed CDC platform for capturing database changes.
- **Debezium UI**: Web interface for managing Debezium connectors.
- **Postgres**: The relational database used for storing financial transaction data.

### Running the Project

1. **Start Docker Services**: 

   Navigate to the project directory and run the following command to start all services:

   ```bash
   docker-compose up -d
   ```

   This will pull the necessary Docker images, create containers, and start the services in detached mode.

2. **Verify Services**:

   After running the services, you can verify their status by running:

   ```bash
   docker-compose ps
   ```

   Ensure that all services are up and running.

3. **Access the Services**:

   - Kafka Control Center: http://localhost:9021
   - Debezium UI: http://localhost:8080
   - Postgres: Accessible via port 5431 (default)

### Shutting Down

To stop and remove all services, networks, and volumes, run:

```bash
docker-compose down
```

### Customization

You can customize the Docker Compose file as needed. For instance, to persist Postgres data across restarts, add a volume for the Postgres service:

```yaml
volumes:
  - postgres_data:/var/lib/postgresql/data
```

## Python Script

The Python script generates fake financial transaction data using the `faker` library and inserts it into the PostgreSQL database. This data can be used to simulate a dynamic environment for testing CDC with Debezium and Kafka.

You can modify the script to change the data schema, transaction frequency, or volume of data.

## Conclusion

This project is a hands-on demonstration of implementing CDC using Debezium, Kafka, and Postgres in a Dockerized setup. It showcases essential skills in data engineering, including real-time data streaming, distributed systems, and containerized development environments.
