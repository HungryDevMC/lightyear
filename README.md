# Lightyear
Horizontally scalable Minecraft server, using Purpur fork and Kafka 

## POC
The basic principle of Lightyear is communicating packets between servers, so that it will give the illusion everyone is one the same server.
Kafka is the medium we will use to communicate these messages through as it can scale very well and will allow us to easily manipulate the data in transit as well.

Technical steps in order to reach this goal:
- When a wrapped packet is sent on a server, we will also put it on a kafka topic (separated per packet name)
- Each server will have a consumer for each packet type topic

## Next steps
- Sync worlds through kafka too? Without this, the setup is only usable for (semi-)static maps.
- Optimizing latency, will having all these consumers per server instance be costly? 
