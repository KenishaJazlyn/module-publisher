a. How many data your publisher program will send to the message broker in one
run?

    It will send 5 data, each publish_event call sends one message.

b. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?
- Protocol: amqp:// - This specifies the protocol used, which is AMQP. It is used for connecting to and communicating with the message broker.
- User Credentials: guest:guest - These are the default username and password for RabbitMQ when it's installed and not yet configured with more secure settings. 'guest' is the username, and the password follows the colon.
- Host: localhost - This part of the URL specifies the hostname or IP address where the RabbitMQ server is running. localhost indicates that the server is running on the same machine as the client software.
- Port: 5672 - This is the default port for non-SSL/TLS connections to RabbitMQ.


Running RabbitMQ as message broker
![img.png](img.png)

Sending and processing event
![img_2.png](img_2.png)
    
    Running the publisher with cargo run triggers the sending of 5 events to the message broker. These events are then picked up by the subscriber. The screenshot above shows the subscriber's console as it receives and processes each event. This demonstrates how the publisher and subscriber interact through RabbitMQ, where messages are queued and then handled by the connected subscriber.

Monitoring chart based on publisher
![img_3.png](img_3.png)

    When the publisher is run, it sends messages (or events) to the RabbitMQ message broker. These messages are queued in RabbitMQ until they are consumed by any connected subscribers. The "spike" that I observe in the RabbitMQ management console’s charts represents a sudden increase in message traffic and queue utilization. Each time the publisher is run, it generates a batch of new messages, which results in an immediate rise in the number of messages within the system.
    When the publisher sends messages, we can see a spike on the RabbitMQ charts. This spike shows that the message broker is receiving and holding more messages for a short time until they are given to the subscribers.


