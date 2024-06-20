# Kafka and Zookeeper Docker Setup

This repository provides a Docker Compose configuration for setting up Apache Kafka and Zookeeper. The setup includes:

- **Zookeeper**: Manages and coordinates the Kafka brokers.
- **Kafka**: Distributed event streaming platform.

## Getting Started

### Clone the Repository

```bash
git clone https://github.com/AdhithyanM/kafka-setup.git
cd <your-repo-directory>
```

### Starting the Services

1. **Start Docker Containers**:

   Run the following command to start the Kafka and Zookeeper services:

   ```bash
   docker-compose up -d
   ```

   This will start the services in detached mode.

2. **Verify the Setup**:

   To ensure that both Kafka and Zookeeper are running, use the following command:

   ```bash
   docker ps
   ```

   You should see containers for both Kafka and Zookeeper.

### Stopping the Services

To stop the services, run:

```bash
docker-compose down
```

### Accessing Kafka and Zookeeper

- **Zookeeper**: Access Zookeeper on port `2181`.
- **Kafka**: Access Kafka on port `9092`.

### Producing and Consuming Messages

1. **Producing Messages**:

   To produce messages to a Kafka topic:

   ```bash
   docker-compose exec kafka kafka-console-producer.sh --topic <topic-name> --bootstrap-server localhost:9092
   ```

   Replace `<topic-name>` with your desired topic name.

2. **Consuming Messages**:

   To consume messages from a Kafka topic:

   ```bash
   docker-compose exec kafka kafka-console-consumer.sh --topic <topic-name> --bootstrap-server localhost:9092 --from-beginning
   ```

   Replace `<topic-name>` with your desired topic name.

### Customization

You can customize the configuration by modifying the `docker-compose.yml` file as needed.

### Troubleshooting

- Ensure Docker and Docker Compose are installed and running.
- Check logs for Kafka and Zookeeper containers if they fail to start:

  ```bash
  docker-compose logs zookeeper
  docker-compose logs kafka
  ```
