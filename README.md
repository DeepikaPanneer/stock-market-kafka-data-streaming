# 📈 Stock Market Data Pipeline using Kafka and AWS

This project demonstrates a real-time stock market data simulation and processing pipeline using Apache Kafka and AWS services. The pipeline includes the following:

- Simulating stock market data using Python
- Streaming data into Apache Kafka on an EC2 instance
- Consuming the data and storing it in Amazon S3
- Crawling and cataloging the S3 data using AWS Glue
- Querying the data with Amazon Athena

---

## 🧰 Technologies Used

- Python
- Apache Kafka (on AWS EC2)
- Amazon S3
- AWS Glue (Crawler + Data Catalog)
- Amazon Athena

---

---

## 🔧 Setup Instructions

### 1. Kafka Setup on EC2

Refer to `command_kafka.txt` for detailed steps. Key highlights:

```bash
# Install Java and Kafka
wget https://archive.apache.org/dist/kafka/3.3.1/kafka_2.12-3.3.1.tgz
tar -xvf kafka_2.12-3.3.1.tgz
cd kafka_2.12-3.3.1
sudo dnf install java-1.8.0-amazon-corretto -y

# Edit config/server.properties:
listeners=PLAINTEXT://0.0.0.0:9092
advertised.listeners=PLAINTEXT://<EC2_PUBLIC_IP>:9092

# Start Zookeeper and Kafka
bin/zookeeper-server-start.sh config/zookeeper.properties
bin/kafka-server-start.sh config/server.properties

# Create a Kafka topic
bin/kafka-topics.sh --create --topic kafka-topic-test --bootstrap-server <EC2_PUBLIC_IP>:9092 --replication-factor 1 --partitions 1




