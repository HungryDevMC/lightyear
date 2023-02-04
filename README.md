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
- Compact messages where possible? 
- Built-in configurable replay system? Messages could be saved to some persistent storage or be read from the topics (depending on retention period) to replay
player packets. This can be used for both recording content and cheater analysis
- Streamer follow mode? We could simply sync the watcher's position with the streamer's position, skin etc so the player will be able to watch what the streamer is doing in-game from a first and third person perspective
- Cross-server dynmap system with all the packet details available
- This is a tricky one, could PvP/PvE be fair cross-server too?
