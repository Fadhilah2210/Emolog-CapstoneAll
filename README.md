# Emolog-Capstone 

**Emolog** adalah aplikasi journaling berbasis AI yang memungkinkan pengguna menulis catatan harian sekaligus menganalisis emosi yang terkandung di dalamnya secara otomatis. Aplikasi ini terdiri dari tiga bagian utama:

- 🖼️ **Frontend**: Aplikasi web interaktif
- 🔧 **Backend**: REST API dan pengelolaan data
- 🤖 **Machine Learning**: Model deteksi emosi Bahasa Indonesia
- 🗄️ **Database**: PostgreSQL untuk menyimpan data pengguna dan catatan

---

## 📁 Struktur Proyek

```
emolog/
├── frontend/                 # Aplikasi client-side (HTML, JS, CSS, Webpack)
├── backend/                  # Backend (Node.js + Express)
├── checkpoint-1315/          # Folder model Machine Learning
├── emolog.sql                # File SQL untuk struktur database PostgreSQL
└── README.md                 # Dokumentasi proyek ini
```

---

## 🚀 Cara Menjalankan Proyek

### 1. 📦 Prasyarat

Pastikan Anda sudah menginstall:

- [Node.js](https://nodejs.org/)
- [npm](https://www.npmjs.com/)
- [PostgreSQL](https://www.postgresql.org/)
- [Python 3.10+](https://www.python.org/)
- [pip](https://pip.pypa.io/en/stable/)

---

### 2. 🗄️ Setup Database

1. Buka PostgreSQL (bisa lewat PgAdmin atau psql CLI).
2. Buat database baru bernama `emolog`.
3. Import file `emolog.sql` ke dalam database:

   ```bash
   psql -U postgres -d emolog -f emolog.sql
   ```

4. Pastikan koneksi database di backend sudah sesuai di `app.js`:
   ```js
   const { Pool } = require('pg')
   const db = new Pool({
     user: 'postgres',
     host: 'localhost',
     database: 'emolog',
     password: 'YOUR_PASSWORD',
     port: 5432
   })
   ```

---

### 3. ⚙️ Jalankan Backend

1. Masuk ke direktori backend:
   ```bash
   cd backend
   ```

2. Install dependensi:
   ```bash
   npm install
   ```

3. Jalankan server:
   ```bash
   npx nodemon app.js
   ```

4. Backend akan berjalan di: `http://localhost:3000`

---

### 4. 🖥️ Jalankan Frontend

1. Masuk ke direktori frontend:
   ```bash
   cd frontend
   ```

2. Install dependensi:
   ```bash
   npm install
   ```

3. Jalankan server:
   ```bash
   npm start
   ```

4. Akses melalui: `http://localhost:8080`

---

### 5. 🤖 Jalankan Model Machine Learning

1. Masuk ke direktori model:
   ```bash
   cd checkpoint-1315
   ```

2. Install dependensi:
   ```bash
   pip install fastapi uvicorn torch transformers
   ```

3. Jalankan API model:
   ```bash
   uvicorn app:app --reload
   ```

4. Akses melalui: `http://localhost:8000`

---

## 🌟 Fitur Aplikasi

- ✍️ Menulis catatan harian
- 😄 Deteksi otomatis emosi pengguna
- 📅 Kalender histori catatan
- 📤 Upload dan simpan gambar
- 🔐 Autentikasi pengguna

---

## 🛠️ Teknologi yang Digunakan

| Bagian     | Teknologi                             |
|------------|----------------------------------------|
| Frontend   | HTML, CSS, JavaScript, Webpack        |
| Backend    | Node.js, Express.js, PostgreSQL       |
| ML Model   | IndoBERT, HuggingFace, FastAPI, PyTorch |
| Database   | PostgreSQL                            |

---

## 📁 Penjelasan Direktori Penting

### Frontend

```
frontend/
├── pages/              # File HTML halaman login, register, home, dsb.
├── script/             # JavaScript per halaman
├── assets/             # Gambar dan style (CSS)
├── webpack.common.js   # Konfigurasi build umum
```

### Backend

```
backend/
├── app.js              # Entry point Express.js
├── src/                # Berisi controller, router, dsb.
├── emolog.sql          # Struktur database PostgreSQL
```

### Model Machine Learning

```
checkpoint-1315/
├── app.py                  # Serve FastAPI untuk deteksi emosi
├── model.safetensors       # Bobot model IndoBERT
├── tokenizer.json          # Tokenizer hasil training
```

---

## 🧪 Contoh Request API ML

```http
POST http://localhost:8000/predict
Content-Type: application/json

{
  "text": "Hari ini aku merasa sangat kesepian."
}
```

Response:
```json
{
  "label": "sedih",
  "score": 0.943
}
```

---

## 🔐 Environment Variable (Opsional)

Untuk mengatur environment:

**backend/.env**
```
PORT=3000
DB_USER=postgres
DB_HOST=localhost
DB_DATABASE=emolog
DB_PASSWORD=your_password
DB_PORT=5432
```

---

## 📚 Lisensi

MIT License © 2025 Emolog Team

---

## 🤝 Kontribusi

Pull request dan feedback sangat terbuka! Silakan fork dan buat perubahan jika ingin berkontribusi.

---

## ✨ Penutup

Emolog menggabungkan teknologi modern untuk mendukung kesehatan mental dengan pendekatan yang humanis dan berbasis data. Selamat mencoba!