# Apache Flink E-Commerce Analytics with Elasticsearch and Postgres
This repository contains an Apache Flink application for real-time sales analytics built using Docker Compose to orchestrate the necessary infrastructure components, including Apache Flink, Elasticsearch, and Postgres. The application processes financial transaction data from Kafka, performs aggregations, and stores the results in both Postgres and Elasticsearch for further analysis.

## Table of contents
- [Requirements](#Requirements)
- [Architecture](#Architecture)
- [Installation and Setup](#Installation)
- [Usage](#Usage)
- [Application](#Application)
- [Components](#Components)

## Requirements
- Docker
- Docker Compose
  
## Architecture
![image](https://github.com/user-attachments/assets/800cc41e-1cb3-4170-94e9-07f1610873f7)

## Installation
  1. Clone this repository.
  2. Navigate to the repository directory.
  3. Run ```docker-compose up -d --build``` to start the required services (Apache Flink, Elasticsearch, Postgres).
  4. The Sales Transaction Generator run ```python main.py``` helps to generate the sales transactions into Kafka.

## Usage
To use the project, follow these steps:
  1. Ensure all Docker containers are up and running.
  2. Download Flink from (https://flink.apache.org/downloads/)
  3. Run the ```FlinkCommerce``` application provided in this repository to perform real-time analytics on financial transactions.

## Application
The ```DataStreamJob``` class within the ```FlinkCommerce``` package serves as the main entry point for the Flink application. The application consumes financial transaction data from Kafka, performs various transformations, and stores aggregated results in both Postgres and Elasticsearch.

## Components
#### Apache Flink
- Sets up the Flink execution environment.
- Connects to Kafka as a source for financial transaction data.
- Processes, transforms, and performs aggregations on transaction data streams.
#### Postgres
- Stores transaction data and aggregated results in tables (transactions, sales_per_category, sales_per_day, sales_per_month).
#### Elasticsearch
- Stores transaction data for further analysis.

## Code Structure
- DataStreamJob.java: Contains the Flink application logic, including Kafka source setup, stream processing, transformations, and sinks for Postgres and Elasticsearch.
- Deserializer, Dto, and utils packages: Include necessary classes and utilities for deserialization, data transfer objects, and JSON conversion.

## Configuration
- Kafka settings (bootstrap servers, topic, group ID) are configured within the Kafka source setup.
- Postgres connection details (URL, username, password) are defined in the jdbcUrl, username, and password variables.

## License
This project is licensed under the [MIT License](LICENSE).
