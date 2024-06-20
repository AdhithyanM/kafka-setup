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

1. **Start the Services**:

   - Navigate to the directory containing the `docker-compose.yml` file and run:
     ```bash
     docker-compose up -d
     ```

2. **Verify the Setup**:
   - Check that both Kafka and Zookeeper are running:
     ```bash
     docker ps
     ```
   - You should see containers for both Kafka and Zookeeper running.

### Stopping the Services

To stop the services, run:

```bash
docker-compose down
```

### Using Kafka CLI Tools

Once your Kafka and Zookeeper services are up and running, you can execute Kafka CLI commands inside the Kafka container.

#### Step 1: Access the Kafka Container

You can access the Kafka container's shell to run commands:

```bash
docker-compose exec broker bash
```

#### Step 2: Run Kafka CLI Commands

Now that you are inside the Kafka container, you can use the Kafka CLI tools to create topics, produce messages, and consume messages.

1. **Create a Topic**:

   ```bash
   kafka-topics --create --topic my-topic --bootstrap-server localhost:9092 --partitions 3 --replication-factor 1
   ```

2. **List Topics**:

   ```bash
   kafka-topics --list --bootstrap-server localhost:9092
   ```

3. **Describe a Topic**:

   ```bash
   kafka-topics --describe --topic my-topic --bootstrap-server localhost:9092
   ```

4. **Produce Messages**:

   - Start a producer to send messages to a topic:
     ```bash
     kafka-console-producer --topic my-topic --bootstrap-server localhost:9092
     ```
   - Type your messages and press Enter to send each one. Use `Ctrl+C` to exit the producer.

5. **Consume Messages**:
   - Start a consumer to read messages from a topic:
     ```bash
     kafka-console-consumer --topic my-topic --bootstrap-server localhost:9092 --from-beginning
     ```

### Example Workflow

Here's a step-by-step example workflow:

1. **Create a Topic**:

   ```bash
   docker-compose exec broker kafka-topics --create --topic test-topic --bootstrap-server localhost:9092 --partitions 3 --replication-factor 1
   ```

2. **List All Topics**:

   ```bash
   docker-compose exec broker kafka-topics --list --bootstrap-server localhost:9092
   ```

3. **Describe the Topic**:

   ```bash
   docker-compose exec broker kafka-topics --describe --topic test-topic --bootstrap-server localhost:9092
   ```

4. **Produce Messages to the Topic**:

   ```bash
   docker-compose exec broker kafka-console-producer --topic test-topic --bootstrap-server localhost:9092
   ```

   - After running the command, type messages and press Enter to send each one.
   - Use `Ctrl+C` to exit the producer.

5. **Consume Messages from the Topic**:
   ```bash
   docker-compose exec broker kafka-console-consumer --topic test-topic --bootstrap-server localhost:9092 --from-beginning
   ```

### Summary

This setup provides a Confluent Kafka and Zookeeper configuration using Docker Compose. By following the steps and commands provided, you can easily manage your Kafka topics and messages using the Kafka CLI tools.
