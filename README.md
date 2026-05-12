# Publisher - Module 9 Event-Driven Architecture

## Understanding Publisher and Message Broker

### a. How much data your publisher program will send to the message broker in one run?
Publisher akan mengirimkan 5 event dalam satu kali run. Setiap event berisi data `UserCreatedEventMessage` dengan field `user_id` dan `user_name`. Jadi total ada 5 pesan yang dikirim ke message broker RabbitMQ melalui queue bernama `user_created`.

### b. The url of: "amqp://guest:guest@localhost:5672" is the same as in the subscriber program, what does it mean?
URL yang sama pada publisher dan subscriber berarti keduanya terhubung ke **message broker RabbitMQ yang sama**. Publisher mengirim pesan ke broker tersebut, dan subscriber menerima pesan dari broker yang sama. Ini adalah inti dari arsitektur event-driven, di mana publisher dan subscriber tidak berkomunikasi langsung satu sama lain, melainkan melalui perantara (message broker). Dengan menggunakan URL yang sama, keduanya dapat bertukar pesan secara tidak langsung melalui RabbitMQ yang berjalan di `localhost` port `5672`.

## Running RabbitMQ as Message Broker

RabbitMQ berjalan sebagai message broker pada port 5672, dan interface management dapat diakses melalui browser di localhost:15672. Berikut adalah tampilan RabbitMQ management interface yang menunjukkan broker sedang berjalan:

![RabbitMQ Running](../screenshoots/rabbitmq_running.png)


## Sending and Processing Event

Ketika publisher dijalankan, publisher mengirimkan 5 event `UserCreatedEventMessage` ke message broker RabbitMQ. Subscriber yang sedang berjalan akan menerima dan memproses setiap event tersebut secara real-time. Publisher dan subscriber tidak berkomunikasi langsung, melainkan melalui RabbitMQ sebagai perantara.

![Sending Event](../screenshoots/sending_event.png)

## Monitoring Chart Based on Publisher

Ketika publisher dijalankan beberapa kali, terlihat spike pada chart Message rates di RabbitMQ management interface. Spike tersebut menunjukkan adanya pesan yang dikirim oleh publisher dan langsung diproses oleh subscriber. Chart kembali ke 0 karena subscriber memproses pesan dengan cepat sehingga tidak ada antrian yang menumpuk.

![Monitoring Chart](../screenshoots/monitoring_chart.png)
