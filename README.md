🛠️ Tech Stack
Proxy/Load Balancer: Nginx (Latest)

Web Server: Nginx (Alpine)

Containerization: Docker & Docker Compose

📋 Prasyarat
Docker & Docker Compose terinstal di mesin lokal.

🚦 Cara Menjalankan
Clone repositori ini:

Bash

git clone [https://github.com/username/simulasi-lb.git](https://github.com/username/simulasi-lb.git)
cd simulasi-lb
Jalankan infrastruktur:

Bash

docker-compose up -d
Periksa status kontainer:

Bash

docker-compose ps
🔍 Cara Verifikasi
1. Cek Header HTTP
Buka browser dan akses http://localhost:8080. Buka Developer Tools (F12) > Network. Klik pada request localhost dan lihat bagian Response Headers. Anda akan melihat:

X-Backend-Server: Menunjukkan IP internal kontainer yang merespons.

2. Cek Logs
Log akses disimpan secara real-time di folder lokal. Gunakan perintah ini untuk memantau distribusi trafik:

Bash

tail -f logs/access.log
3. Simulasi Health Check
Matikan salah satu kontainer backend untuk melihat bagaimana Load Balancer menangani kegagalan:

Bash

docker stop <nama_container_backend>
Nginx akan secara otomatis berhenti mengirim trafik ke kontainer tersebut tanpa menyebabkan downtime pada sisi pengguna.

📂 Struktur Proyek
nginx.conf: Konfigurasi utama Load Balancer.

default.conf: Konfigurasi server untuk sisi backend.

index.html: Landing page sederhana untuk verifikasi visual.

docker-compose.yml: Definisi layanan dan replika.

logs/: Folder penyimpanan log akses.
