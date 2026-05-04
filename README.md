# Publisher - Module 9 Event-Driven Architecture

## Understanding Publisher and Message Broker

### a. How much data your publisher program will send to the message broker in one run?
Publisher akan mengirimkan 5 event dalam satu kali run. Setiap event berisi data `UserCreatedEventMessage` dengan field `user_id` dan `user_name`. Jadi total ada 5 pesan yang dikirim ke message broker RabbitMQ melalui queue bernama `user_created`.

### b. The url of: "amqp://guest:guest@localhost:5672" is the same as in the subscriber program, what does it mean?
URL yang sama pada publisher dan subscriber berarti keduanya terhubung ke **message broker RabbitMQ yang sama**. Publisher mengirim pesan ke broker tersebut, dan subscriber menerima pesan dari broker yang sama. Ini adalah inti dari arsitektur event-driven, di mana publisher dan subscriber tidak berkomunikasi langsung satu sama lain, melainkan melalui perantara (message broker). Dengan menggunakan URL yang sama, keduanya dapat bertukar pesan secara tidak langsung melalui RabbitMQ yang berjalan di `localhost` port `5672`.