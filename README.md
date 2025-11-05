E-Commerce Hirawr (Laravel)

Proyek e-commerce berbasis Laravel untuk katalog produk, keranjang, checkout, dan manajemen pesanan. Dirancang agar mudah dijalankan secara lokal dan siap dikembangkan menjadi aplikasi produksi.

🔧 Tech Stack

Backend: Laravel (PHP 8.2+)

Frontend: Blade + Vite + Tailwind CSS

Database: MySQL/MariaDB (atau SQLite untuk dev cepat)

Build tools: Vite, NPM

Auth: Laravel Breeze/Fortify/Default Auth (sesuaikan dengan yang terpasang)

Catatan: pastikan versi PHP, Composer, Node sesuai dengan environment kamu.

🚀 Fitur (ringkas)

Katalog produk (listing, detail, pencarian dasar)

Keranjang belanja

Checkout dan pembuatan pesanan

Manajemen akun pengguna (login/registrasi)

Panel admin dasar untuk kelola produk & pesanan (jika modul admin tersedia)

Upload gambar produk dengan storage Laravel

Jika repo kamu belum memiliki semua fitur di atas, gunakan daftar ini sebagai target pengembangan. Hapus yang belum ada agar README tetap jujur.

🗂️ Struktur Direktori Penting
app/
 ├─ Http/Controllers/       # Controller Web & Admin
 ├─ Models/                 # Eloquent Models (Product, Order, dll)
bootstrap/
config/
database/
 ├─ migrations/             # Skema tabel
 └─ seeders/                # Seeder data awal
public/                      # Aset publik (index.php, storage symlink)
resources/
 ├─ views/                  # Blade templates (frontend & admin)
 ├─ css/, js/               # Entry Vite
routes/
 ├─ web.php                 # Route web
 └─ api.php                 # Route API bila ada

🧑‍💻 Menjalankan Secara Lokal
1) Clone & install dependencies
git clone https://github.com/iceguya/E-Commerce-Hirawr.git
cd E-Commerce-Hirawr
composer install
npm install

2) Environment
cp .env.example .env
php artisan key:generate


Atur koneksi database di .env:

APP_NAME="E-Commerce Hirawr"
APP_ENV=local
APP_KEY=base64:... # otomatis diisi
APP_URL=http://localhost

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=hirawr
DB_USERNAME=root
DB_PASSWORD=yourpassword

# Opsional: jika pakai SQLite untuk cepat
# DB_CONNECTION=sqlite
# (buat file database/database.sqlite dan ubah config/database.php bila perlu)

3) Database: migrate & seed
php artisan migrate
php artisan db:seed


Jika ada seeder admin, akan dibuat akun admin. Cek bagian Akun Default (Dev) di bawah.

4) Storage link (untuk upload gambar)
php artisan storage:link

5) Jalankan server & bundler

Di terminal 1:

php artisan serve


Di terminal 2:

npm run dev


Akses di: http://127.0.0.1:8000

👤 Akun Default (Dev)

Jika seeder menambahkan user/admin, gunakan kredensial berikut (sesuaikan dengan seeder kamu):

Admin
Email    : admin@example.com
Password : password

User
Email    : user@example.com
Password : password


Jika password tidak cocok, cek database/seeders/*Seeder.php untuk melihat nilai yang di-hash, lalu set ulang sesuai kebutuhan:
php artisan tinker → bcrypt('password-baru')
