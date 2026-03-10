# Nginx Load Balancing Simulation with Docker

Proyek ini adalah simulasi infrastruktur **High Availability** menggunakan **Nginx** sebagai Load Balancer dan **Docker Compose** untuk orkestrasi kontainer. Proyek ini dirancang untuk menunjukkan pemahaman tentang distribusi trafik, *health checking*, dan *observability* dalam lingkungan DevOps.



## 🚀 Fitur Utama

* **Round Robin Load Balancing**: Mendistribusikan trafik secara merata ke beberapa replika backend.
* **Health Checks**: Memastikan trafik hanya dikirim ke kontainer yang sehat.
* **Custom Logging**: Format log kustom untuk memantau aktivitas *upstream server*.
* **Visibility**: Header HTTP kustom (`X-Backend-Server`) untuk melacak server mana yang melayani permintaan.
* **Infrastructure as Code**: Seluruh setup didefinisikan dalam file konfigurasi yang mudah dikelola.

## 🏗️ Arsitektur
Trafik masuk melalui port `8080` pada host, diterima oleh Nginx Load Balancer, lalu diteruskan ke salah satu dari 3 replika kontainer backend (Nginx-Alpine).

```text
User Request (8080) -> [ Nginx Load Balancer ]
                             |
              -------------------------------
              |              |              |
      [ Backend 1 ]    [ Backend 2 ]    [ Backend 3 ]