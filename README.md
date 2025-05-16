## How much data does your publisher program send to the message broker in one run?

In one run, the publisher sends 5 messages to the message broker. Each message is an instance of UserCreatedEventMessage, which includes two string fields: user_id and user_name.
The total amount of data depends on the serialized size of each message, but roughly it would be around a few hundred bytes in total, assuming short string values.

## The URL amqp://guest:guest@localhost:5672 is the same as in the subscriber program. What does it mean?

- amqp://: Specifies the protocol used — AMQP (Advanced Message Queuing Protocol).

- guest:guest: Represents the default username and password to authenticate with the message broker.

- localhost: Refers to the host where the RabbitMQ broker is running — in this case, it’s the local machine.

- 5672: The default port used by RabbitMQ for AMQP connections (non-SSL).

So, the full URL tells the publisher or subscriber to connect to a local RabbitMQ instance using default credentials over the AMQP protocol.

## RabbitMQ Running Screenshot

The following screenshot shows RabbitMQ running locally on Docker:

![RabbitMQ Screenshot](screenshot/rabbitmq.png)

## Running the Publisher and Subscriber

When I run the publisher using `cargo run`, it sends 5 events to the message broker (RabbitMQ).  
Each event contains a user ID and user name as part of the `UserCreatedEventMessage` structure.

The subscriber, which is already running in a separate terminal, listens to the `"user_created"` queue.  
After the publisher sends the events, the subscriber receives and processes them one by one.

Below is a screenshot of the publisher sending events and the subscriber receiving them:

Publisher
![Publisher](screenshot/publisher.png)

Subscriber
![Subscriber](screenshot/subscriber.png)

