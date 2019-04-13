# Projet - Fonctionnal Data Programming

**Romain Beaussart**

## Launch our project

1. Launch the Zookeeper server

```powershell
$ bin/zookeeper-server-start.sh config/zookeeper.properties
```

2. Launch the Kafka server

```powershell
$ bin/kafka-server-start.sh ./config/server.properties
```

3. Change the link of the file in `SendData.scala`

4. If you want to see the stream

```powershell
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 \
--topic busNetwork \
--from-beginning \
--property print.key=true \
```



### Info

#### Topics creation

```powershell
bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic busNetwork
```



## Structure

`busNetwork` is the name of the Kafka topic used

`SendData.scala` is the administrator application. It is used to retrieve all the information from all the buses, and thus see if they are full, and what their fuel level is.

In the `Spark/src/main/resources/history`folder, you have the full history of all the buses. The name of the file corresponds to the date of generation of the file.



### Bus class

![BusClass](Others/Untitled%20Diagram.png)



### busData.csv and the other files in the `history` folder

The data in the csv files are distributed in this way:

| Name         | RemainingFuel                                  | Accident                              | NumberOfSeatsRemaining                   |
| ------------ | ---------------------------------------------- | ------------------------------------- | ---------------------------------------- |
| The bus name | The remaining amount of fuel oil in percentage | If the bus is involved in an accident | The number of seats remaining on the bus |


