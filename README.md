## How much data does your publisher program send to the message broker in one run?

In one run, the publisher sends 5 messages to the message broker. Each message is an instance of UserCreatedEventMessage, which includes two string fields: user_id and user_name.
The total amount of data depends on the serialized size of each message, but roughly it would be around a few hundred bytes in total, assuming short string values.

## The URL amqp://guest:guest@localhost:5672 is the same as in the subscriber program. What does it mean?

- amqp://: Specifies the protocol used — AMQP (Advanced Message Queuing Protocol).

- guest:guest: Represents the default username and password to authenticate with the message broker.

- localhost: Refers to the host where the RabbitMQ broker is running — in this case, it’s the local machine.

- 5672: The default port used by RabbitMQ for AMQP connections (non-SSL).

So, the full URL tells the publisher or subscriber to connect to a local RabbitMQ instance using default credentials over the AMQP protocol.