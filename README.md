# Kafka-Docker-Setup-With-Demo
This is a demo project showing how to create a stream data processing system

# check list

- setting up zookeeper and kafka with docker 

- creating clients that talk to the kafka broker

The demo project is a fraud detection system. It will have two clients.
One of the clients will be a producer generating the transactions as a stream of data.
The other one will consumen those transaction events, check if they are fradulent, and publish them on separate topics based on the result from the checking.

![image](https://user-images.githubusercontent.com/39389971/177281929-47bb7e5b-de9d-41f5-a316-ee338fa3f11e.png)

This repo is built using [this](https://dev.to/florimondmanca/breaking-news-everything-is-an-event-streams-kafka-and-you-2n9j)  blog post. 
[Building A Streaming Fraud Detection System With Kafka And Python](https://dev.to/florimondmanca/breaking-news-everything-is-an-event-streams-kafka-and-you-2n9j)

![Topics](https://res.cloudinary.com/practicaldev/image/fetch/s--gkM6dgTn--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://florimondmanca-personal-website.s3.amazonaws.com/media/markdownx/288f76de-ccdb-4be3-83d8-672e0f9dd326.png)
# Instructions

1. Clone the repo
   ```bash
   git clone https://github.com/STT-Data-Engineering/Kafka-Docker-Setup-With-Demo.git
   ```
2. Create the docker network that the broker and clients would communicate with
   ```bash
   docker network create kafka-network
   ```
3. Start zookeeper and kafka containers
   ```bash
   docker-compose -f docker-compose.kafka.yml up
   ```
4. Start The clients with another terminal window
   ```bash
   docker-compose up
   ```

To inspect if the clients are really communicating with the broker, you can use the following:

To check the generator:
```bash
docker-compose -f docker-compose.kafka.yml exec broker kafka-console-consumer --bootstrap-server localhost:9092 --topic queueing.transactions --from-beginning
```

To check the detector:
```bash
docker-compose -f docker-compose.kafka.yml exec broker kafka-console-consumer --bootstrap-server localhost:9092 --topic streaming.transactions.legit
```

and

```bash
docker-compose -f docker-compose.kafka.yml exec broker kafka-console-consumer --bootstrap-server localhost:9092 --topic streaming.transactions.fraud
```