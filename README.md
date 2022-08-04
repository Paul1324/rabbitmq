# RabbitMQ

RabbitMQ este un message broker ce primeste mesaje de la aplicatii numite publisheri si le directioneaza catre aplicatii cu rolul de procesare al mesajelor (consumer).  
Publisher-ul, consumer-ul si messsage broker-ul pot sa se afle pe servere separate.

## Rolul unui message broker

- Face conexiunea intre aplicatii diferite
- Load balancing
- Backup in cazul in care consumerul nu mai functioneaza

## Protocoale suportate

- [AMQP 0-9-1](https://www.rabbitmq.com/tutorials/amqp-concepts.html)
- [STOMP](http://stomp.github.io/)
- [MQTT](https://mqtt.org/)
- [AMQP 1.0](https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-amqp-overview)
- [HTTP si WebSockets](https://www.rabbitmq.com/protocols.html#http-and-websockets)
- [RabbitMQ Streams](https://github.com/rabbitmq/rabbitmq-server/blob/v3.10.x/deps/rabbitmq_stream/docs/PROTOCOL.adoc)

## Protocolul AMQP 0-9-1

![Protocol AMQP](https://www.rabbitmq.com/img/tutorials/intro/hello-world-example-routing.png)  
Mesajele sunt publicate catre un exchange. Exchange-ul distribuie mesajele catre cozi (queues), urmarind anumite reguli numite bindings.

## Publisher

## Exchange

### Default exchange

Toate cozile de asteptare create sunt legate automat de el printr-un routing key cu acelasi nume ca queue-ul.

### Fanout exchange

Distribuie mesajele catre toate cozile de asteptare legate de acesta, iar routing key-ul este ignorat.
![Fanout exchange](https://www.rabbitmq.com/img/tutorials/intro/exchange-fanout.png)

### Direct exchange

Distribuie mesaje catre queue-ul specificat prin routing key.
![Direct exchange](https://www.rabbitmq.com/img/tutorials/intro/exchange-direct.png)

### Topic exchange

Distribuie mesajele catre queue-uri, asigurandu-se ca routing-key-ul din mesaj se potriveste tiparului folosit pentru stabilirea legaturii dintre queue si exchange.  
![Topic exchange](https://www.rabbitmq.com/img/tutorials/python-five.png)

## Queue

Stocheaza mesaje.

### Proprietati principale

- nume
- durable (persista in urma restartarii broker-ului)
- auto-delete (se sterge automat atunci cand nu mai sunt consumeri conectati la coada)

## Consumer

Există două tipuri de moduri in care un consumer poate sa functioneze:

- prin push API (aplicatiile trebuie sa isi declare interesul in a consuma mesaje), fiecare consumer inregistrat primind un consumer tag (string).
- prin pull API ( este recomandata evitarea acestei variante).

## Tutoriale

- [AMQP 0-9-1](https://www.rabbitmq.com/tutorials/amqp-concepts.html)
- [RabbitMQ tutorials](https://www.rabbitmq.com/getstarted.html)
- [Supported Protocols](https://www.rabbitmq.com/protocols.html)
- https://www.rabbitmq.com/amqp-0-9-1-quickref.html
