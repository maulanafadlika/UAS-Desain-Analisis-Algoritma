# **Analisis Program Pemantauan Vitamin dan Suplemen Berbasis Website**

## **Latar Belakang**

Kesehatan sangat penting, dan mengonsumsi vitamin serta suplemen yang tepat adalah cara yang umum digunakan untuk menjaga tubuh tetap sehat. Namun, banyak orang kesulitan untuk mengatur konsumsi suplemen yang benar, baik dalam hal dosis maupun waktu.

Pemantauan konsumsi suplemen secara manual sering kali kurang efisien dan bisa berisiko. Untuk mengatasi masalah ini, dibutuhkan aplikasi berbasis website yang memudahkan pengguna dalam mencatat konsumsi suplemen, mengingatkan waktu konsumsi, serta memberikan laporan yang terorganisir.

Program pemantauan vitamin dan suplemen berbasis website ini hadir untuk membantu pengguna dalam memantau konsumsi suplemen mereka. Dengan memanfaatkan **Filament** untuk membangun antarmuka yang mudah digunakan dan **Docker** untuk memastikan aplikasi berjalan dengan stabil di berbagai platform, program ini memberikan kemudahan dalam pengelolaan konsumsi suplemen secara efisien.

## **1. Tujuan Program**
Program ini bertujuan untuk:
- **Mencatat konsumsi suplemen dan vitamin** yang digunakan oleh pengguna.
- **Memberikan pengingat otomatis** terkait waktu konsumsi suplemen.
- **Menampilkan grafik dan laporan** tentang konsumsi vitamin dan suplemen yang dikonsumsi, memungkinkan pengguna untuk memantau status kesehatan mereka.

## **2. Teknologi yang Digunakan**

### **Filament**
Filament adalah framework untuk Laravel yang menyediakan antarmuka admin yang cepat dan elegan. Framework ini berguna untuk membangun dashboard administrasi yang mudah diakses dan digunakan oleh pengguna akhir. Dengan menggunakan Filament, pengelolaan data menjadi lebih terstruktur dan efisien. Fitur utama yang digunakan dalam aplikasi ini antara lain:
- **CRUD (Create, Read, Update, Delete)** untuk memanage data vitamin dan suplemen.
- **Autentikasi pengguna** untuk memastikan data hanya dapat diakses oleh pengguna yang berhak.
- **Dashboard interaktif** untuk menampilkan data pemantauan konsumsi secara visual.

### **Docker**
Docker digunakan untuk menjalankan aplikasi dalam **kontainer**, yang memungkinkan aplikasi untuk berjalan dengan lebih konsisten di berbagai lingkungan tanpa masalah kompatibilitas. Beberapa keuntungan menggunakan Docker:
- **Isolasi aplikasi**: Setiap komponen aplikasi berjalan di kontainer terpisah, memastikan aplikasi utama dan dependensinya tidak saling mengganggu.
- **Portabilitas**: Aplikasi dapat dipindahkan dan dijalankan di server atau komputer lain yang memiliki Docker tanpa memerlukan konfigurasi ulang.
- **Pengelolaan sumber daya**: Docker memungkinkan pengaturan sumber daya aplikasi yang lebih efisien, seperti memori dan CPU.

## **3. Analisis Alur Peran Pengguna***

1. Pengguna Umum
   - Mendaftar dan login ke sistem.
   - Menambahkan vitamin atau suplemen yang dikonsumsi.
   - Mengatur jadwal konsumsi dan mengaktifkan pengingat.
   - Melihat riwayat konsumsi dan menerima analisis pola konsumsi.

2. Admin
  - Mengelola daftar vitamin dan suplemen yang tersedia dalam sistem.
  - Mengelola pengguna (verifikasi, penghapusan akun jika diperlukan).
  - Memantau performa sistem dan memastikan layanan berjalan dengan baik.**

## **Alur Kerja Program**

1. **Pendaftaran Pengguna**: Pengguna mendaftar melalui aplikasi untuk membuat akun pribadi.
2. **Pencatatan Suplemen**: Pengguna menambahkan informasi mengenai suplemen dan vitamin yang mereka konsumsi, termasuk dosis, waktu konsumsi, dan jenis suplemen.
3. **Pengingat Konsumsi**: Aplikasi mengirimkan pengingat untuk konsumsi suplemen pada waktu yang telah ditentukan.
4. **Laporan & Statistik**: Aplikasi memberikan laporan mengenai konsumsi vitamin dan suplemen yang dikonsumsi, termasuk grafik yang menunjukkan konsumsi berdasarkan waktu.

---

### Usecase Alur Program

![alt text](image-1.png)


## **Flowchart Alur Kerja Program**

![alt text](image.png)

## **4. Keuntungan Penggunaan Filament dan Docker**

### **Keuntungan Filament**
- **Kemudahan Pengembangan**: Filament menyediakan komponen yang sudah siap pakai untuk membangun antarmuka pengguna dan admin dengan cepat.
- **Desain yang Responsif**: Filament mendukung tampilan yang responsif, memudahkan akses aplikasi di berbagai perangkat.
- **Integrasi dengan Laravel**: Menggunakan Filament bersama Laravel memudahkan pengelolaan aplikasi secara backend dengan sistem yang sudah dikenal.

### **Keuntungan Docker**
- **Kontainerisasi**: Dengan Docker, kita dapat mengisolasi aplikasi dari sistem host dan menjalankannya di berbagai platform tanpa masalah kompatibilitas.
- **Skalabilitas**: Docker memungkinkan kita untuk dengan mudah menskalakan aplikasi dengan menambahkan lebih banyak kontainer untuk menangani beban lebih besar.
- **Kemudahan Deployment**: Docker menyederhanakan proses deployment karena kita hanya perlu membagikan image Docker daripada harus mengonfigurasi lingkungan dari awal.

## **5. Tantangan dan Solusi**

### **Tantangan**
- **Pemantauan Konsumsi yang Tepat**: Menyediakan pengingat yang tepat untuk setiap pengguna sesuai dengan jadwal konsumsi mereka bisa menjadi tantangan.
- **Kebutuhan untuk Pengelolaan Data yang Akurat**: Dengan banyaknya data yang harus ditangani, pengelolaan dan keamanan data menjadi hal yang sangat penting.

### **Solusi**
- **Fitur Penjadwalan**: Pengingat otomatis akan disesuaikan dengan waktu konsumsi yang telah ditentukan pengguna.
- **Enkripsi dan Keamanan**: Menggunakan enkripsi untuk melindungi data sensitif pengguna, serta implementasi autentikasi dua faktor (2FA) untuk menambah lapisan keamanan.

## **Rancangan Database Pemantauan Vitamin dan Suplemen**

### **1. Tabel `users` (Pengguna)**
| Kolom      | Tipe Data            | Deskripsi                                    |
|------------|----------------------|----------------------------------------------|
| id         | BIGINT (PK, AI)       | ID unik pengguna.                           |
| name       | VARCHAR(255)          | Nama lengkap pengguna.                      |
| email      | VARCHAR(255) (UNIK)   | Email pengguna.                             |
| password   | VARCHAR(255)          | Password terenkripsi.                       |
| role       | ENUM('user', 'admin') | Menentukan peran pengguna (user atau admin). |
| created_at | TIMESTAMP             | Waktu pembuatan akun.                       |
| updated_at | TIMESTAMP             | Waktu terakhir update akun.                 |

### **2. Tabel `supplements` (Suplemen)**
| Kolom       | Tipe Data                               | Deskripsi                                   |
|-------------|----------------------------------------|---------------------------------------------|
| id          | BIGINT (PK, AI)                        | ID unik suplemen.                          |
| user_id     | BIGINT (FK)                            | ID pengguna (relasi ke `users.id`).        |
| name        | VARCHAR(255)                           | Nama suplemen.                             |
| dosage      | VARCHAR(255)                           | Dosis konsumsi suplemen.                   |
| frequency   | ENUM('harian', 'mingguan', 'bulanan')  | Frekuensi konsumsi.                        |
| start_date  | DATE                                   | Tanggal mulai konsumsi suplemen.           |
| end_date    | DATE (Opsional)                        | Tanggal berakhir konsumsi (jika ada).      |
| created_at  | TIMESTAMP                              | Waktu pencatatan suplemen.                 |
| updated_at  | TIMESTAMP                              | Waktu terakhir update.                     |

### **3. Tabel `reminders` (Pengingat)**
| Kolom         | Tipe Data           | Deskripsi                                    |
|--------------|--------------------|----------------------------------------------|
| id           | BIGINT (PK, AI)     | ID unik pengingat.                          |
| user_id      | BIGINT (FK)         | ID pengguna (relasi ke `users.id`).         |
| supplement_id| BIGINT (FK)         | ID suplemen (relasi ke `supplements.id`).   |
| reminder_time| TIME                | Waktu pengingat konsumsi suplemen.          |
| status       | ENUM('aktif', 'nonaktif') | Status pengingat.                     |
| created_at   | TIMESTAMP           | Waktu pembuatan pengingat.                  |
| updated_at   | TIMESTAMP           | Waktu terakhir update pengingat.            |

### **4. Tabel `reports` (Laporan Konsumsi)**
| Kolom         | Tipe Data           | Deskripsi                                    |
|--------------|--------------------|----------------------------------------------|
| id           | BIGINT (PK, AI)     | ID unik laporan konsumsi.                   |
| user_id      | BIGINT (FK)         | ID pengguna (relasi ke `users.id`).         |
| supplement_id| BIGINT (FK)         | ID suplemen (relasi ke `supplements.id`).   |
| consumption_date | DATE            | Tanggal konsumsi suplemen.                  |
| status       | ENUM('diminum', 'terlewat') | Status konsumsi.                   |
| created_at   | TIMESTAMP           | Waktu pencatatan laporan.                   |
| updated_at   | TIMESTAMP           | Waktu terakhir update laporan.              |

### **5. Tabel `notifications` (Notifikasi)**
| Kolom      | Tipe Data            | Deskripsi                                    |
|------------|----------------------|----------------------------------------------|
| id         | BIGINT (PK, AI)       | ID unik notifikasi.                         |
| user_id    | BIGINT (FK)           | ID pengguna (relasi ke `users.id`).         |
| message    | TEXT                  | Isi notifikasi.                             |
| status     | ENUM('terkirim', 'dibaca') | Status notifikasi.                     |
| created_at | TIMESTAMP             | Waktu pengiriman notifikasi.                |

---

## Relasi Database

Berikut adalah penjelasan mengenai relasi antar tabel dalam database:

### 1. Relasi antara `users` dan `supplements`
- **`users (1) → (M) supplements`**  
  Setiap pengguna (`users`) dapat memiliki banyak suplemen (`supplements`), namun setiap suplemen hanya dapat dimiliki oleh satu pengguna.

### 2. Relasi antara `users` dan `reminders`
- **`users (1) → (M) reminders`**  
  Setiap pengguna (`users`) dapat memiliki banyak pengingat (`reminders`), namun setiap pengingat hanya berkaitan dengan satu pengguna.

### 3. Relasi antara `users` dan `reports`
- **`users (1) → (M) reports`**  
  Setiap pengguna (`users`) dapat memiliki banyak laporan (`reports`), namun setiap laporan hanya terkait dengan satu pengguna.

### 4. Relasi antara `users` dan `notifications`
- **`users (1) → (M) notifications`**  
  Setiap pengguna (`users`) dapat menerima banyak notifikasi (`notifications`), namun setiap notifikasi hanya terkait dengan satu pengguna.

### 5. Relasi antara `supplements` dan `reminders`
- **`supplements (1) → (M) reminders`**  
  Setiap suplemen (`supplements`) dapat memiliki banyak pengingat (`reminders`), tetapi setiap pengingat hanya terkait dengan satu suplemen.

### 6. Relasi antara `supplements` dan `reports`
- **`supplements (1) → (M) reports`**  
  Setiap suplemen (`supplements`) dapat memiliki banyak laporan (`reports`), namun setiap laporan hanya berkaitan dengan satu suplemen.

### 7. Relasi antara `reminders` dan `supplements`
- **`reminders (M) ← (1) supplements`**  
  Setiap pengingat (`reminders`) berkaitan dengan satu suplemen, tetapi setiap suplemen dapat memiliki banyak pengingat.

### 8. Relasi antara `reports` dan `supplements`
- **`reports (M) ← (1) supplements`**  
  Setiap laporan (`reports`) berkaitan dengan satu suplemen, tetapi setiap suplemen dapat memiliki banyak laporan.

### 9. Relasi antara `notifications` dan `users`
- **`notifications (M) ← (1) users`**  
  Setiap notifikasi (`notifications`) berkaitan dengan satu pengguna (`users`), tetapi setiap pengguna dapat menerima banyak notifikasi.

---

## **Kesimpulan**
Penggunaan **Filament** dan **Docker** dalam aplikasi pemantauan vitamin dan suplemen berbasis website memberikan keuntungan besar dalam hal pengembangan dan manajemen aplikasi yang efisien. Filament menyederhanakan pembuatan antarmuka yang user-friendly, sementara Docker memberikan isolasi dan portabilitas aplikasi yang sangat dibutuhkan dalam pengembangan dan deployment aplikasi.
