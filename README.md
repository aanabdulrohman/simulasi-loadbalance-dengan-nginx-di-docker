# 🚀 Nginx Load Balancer with Automated CI/CD & GitOps

Proyek ini mendemonstrasikan implementasi infrastruktur modern yang berfokus pada **High Availability** dan **Automated Deployment**. Bukan sekadar load balancer biasa, proyek ini telah diintegrasikan dengan pipeline CI/CD penuh menggunakan prinsip GitOps.

## 🏗️ Architecture Overview

Sistem ini dirancang dengan alur kerja otomatis sebagai berikut:
1. **Developer** melakukan `git push` kode terbaru ke GitHub.
2. **GitHub Actions** mendeteksi perubahan, lalu menjalankan proses:
   - **Linting & Testing** (Memastikan konfigurasi valid).
   - **Build Docker Image** (Membungkus aplikasi menjadi kontainer).
   - **Push to Registry** (Mengirim image ke Docker Hub).
3. **Watchtower (CD Agent)** di server memantau Docker Hub secara real-time.
4. **Automated Deployment**: Watchtower mendeteksi image baru, menariknya (pull), dan melakukan *restart* kontainer secara otomatis tanpa intervensi manual.

## 🛠️ Tech Stack

- **Load Balancer:** Nginx
- **Containerization:** Docker & Docker Compose
- **CI Tool:** GitHub Actions
- **Registry:** Docker Hub
- **CD Agent:** Watchtower (GitOps approach)
- **Security:** GitHub Secrets for Credential Management

## 🚀 Fitur Utama

- **Load Balancing:** Distribusi trafik ke beberapa backend server untuk skalabilitas.
- **Automated Pipeline:** Automasi penuh dari kode hingga deployment (CI/CD).
- **Security Best Practices:** Menggunakan GitHub Secrets untuk mengamankan kredensial Docker Hub.
- **Self-Healing & Auto-Update:** Sistem otomatis memperbarui dirinya sendiri ketika ada versi terbaru di registry.

## ⚙️ Cara Menjalankan

### 1. Prasyarat
- Docker & Docker Compose terinstal.
- Akun Docker Hub.

### 2. Menjalankan Aplikasi & Load Balancer
```bash
docker-compose up -d