Advance Programming
# Module 9 - Software Architectures (Publisher) 📘

- Nama    : Akhyar Rasyid Asy syifa
- Kelas   : Advance Programming - A
- NPM     : 2306241682

## Reflection
**1. How much data your publisher program will send to the message broker in one run?**

Dalam satu eksekusi function `main()`, program mengirim 5 pesan bertipe `UserCreatedEventMessage` ke RabbitMQ, karena terdapat `publish_event` yang dijalankan sebanyak 5 kali. masing-masing berisi dua string pendek (`user_id` dan `user_name`) yang diserialisasi dengan Borsh. Dengan menggunakan Borsh serialization, perkiraan ukuran setiap pesan sekitar 20-30 byte sehingga total data yang dikirim adalah sekitar 100-150 bytes. Jumlah ini belum termasuk overhead dari protokol AMQP, namun cukup mewakili besar data utama yang dikirim.

**2. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?**

URL `amqp://guest:guest@localhost:5672` digunakan oleh publisher dan subscriber agar keduanya terhubung ke server AMQP yang sama. Bagian `guest:guest` menunjukkan kredensial (username dan password), sementara `localhost:5672` adalah alamat dan port server RabbitMQ yang digunakan. Jika URL berbeda, subscriber tidak akan bisa menerima pesan dari publisher karena mereka akan terhubung ke sesi atau instance server yang berbeda, sehingga tidak saling bertukar pesan.

**Running RabbitMQ as message broker**
![Image](https://github.com/user-attachments/assets/95b4fda4-6177-4f8e-a8c4-c8cd57e8cb51)
