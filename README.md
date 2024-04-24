# Publisher App
Favian Naufal - **2006597802**


## Reflection
**Q** : How many data your publlsher program will send to the message broker in one run?  

**A** : According to the content within the `main.rs` file (line 21-35), there should be 5 data to be sended to the message broker in one run, by running the main function of the file. It can be seen that the method `publish_event()` were called five times within the `main()` method.

---
**Q** : The url of: `amqp://guest:guest@localhost:5672` is the same as in the subscriber program, what does it mean? 

**A** : since the method that uses the same string is `new_queue_publisher()` instead of `new_queue_listener()` like the one in the Subscriber's codebase, it should mean that it would publish messages out of its stack using the url it was provided within its parameter. Since it's using the same url as the one in the Subscriber's codebase, it should mean the message to be sent was done within the same protocol (`amqp`), the same credentials (`guest:guest`) and in the same machine (`localhost`) and its port (`5672`).

---
### Running RabbitMQ
![Running RabbitMQ](image.png)

---
### Sending and processing event
![Sending and processing event](image-1.png)

The screen capture above shows that the five messages were succesfully sent by the publisher (by running the program with `cargo run`), while the subscriber also got all of those five messages succesfully through an event listener. As one can see, the messages were sent through the amqp protocol within the same machine and port (localhost:5672).

---
### Monitoring chart based on publisher
![Monitoring chart based on publisher](image-2.png)

It was shown in the screen capture above that the message broker RabbitMQ accepts and forwards messages, as it records the transactions happened within the chart.

On the top right of the screen also show that the charts update for every 5 seconds, which means that there are 5 messages that was sent in each of those two spikes period as it was shown on the *1.0/s* peak of the spike on the chart.