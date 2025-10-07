Apache Kafka 4.1.0 - Windows Setup Guide
This guide will help you set up Apache Kafka 4.1.0 on Windows without Docker.

✅ Kafka 4.1.0 Setup on Windows (No Docker)
Step 1: Check Java Version
Kafka requires Java 17+. Run in Command Prompt:

cmd
java -version
If you see a version less than 17, install the latest JDK first from Oracle's website.

Step 2: Generate a Cluster UUID
Open Command Prompt and navigate to your Kafka folder:

cmd
cd D:\KAFKA\kafka_2.13-4.1.0
bin\windows\kafka-storage.bat random-uuid
👉 This will output something like:

text
F4j2R1sXQEa9d1lZw2a9Vg
That's your Kafka Cluster ID. Copy it.

Step 3: Format Log Directories
Use the cluster ID you just generated:

cmd
bin\windows\kafka-storage.bat format -t F4j2R1sXQEa9d1lZw2a9Vg -c config\kraft\server.properties
This initializes Kafka's storage with your cluster ID.

Step 4: Start Kafka Server
Finally, start the server:

cmd
bin\windows\kafka-server-start.bat config\kraft\server.properties
If successful, you'll see logs like:

text
INFO [KafkaServer id=0] started (kafka.server.KafkaServer)
That means Kafka is running on port 9092 by default. 🎉

✅ Alternative: Run Kafka with Docker (Windows)
If you have Docker Desktop installed, you can skip all the steps above and just run:

cmd
docker pull apache/kafka:4.1.0
docker run -p 9092:9092 apache/kafka:4.1.0
👉 This is easier but requires Docker.

⚠️ Quick Notes
On Windows, always use bin\windows\*.bat instead of bin/*.sh

Kafka logs will appear in your terminal - keep it open while using Kafka

If you want Kafka + ZooKeeper (old style), you'd use zookeeper-server-start.bat and then kafka-server-start.bat

But in Kafka 4.1.0 (KRaft mode) you don't need ZooKeeper

🔧 Next Steps
Once Kafka is running, you can:

Create topics using Kafka command-line tools

Configure Spring Boot applications to connect to localhost:9092

Start producing and consuming messages

📚 Resources
Apache Kafka Documentation

Spring for Apache Kafka
