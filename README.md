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
