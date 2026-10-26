# 🤖 Panduan Instalasi AI Agent Lokal

Panduan lengkap ini akan membantu Anda menginstal dan menjalankan AI Agent secara offline/lokal di komputer atau laptop menggunakan `llama.cpp` dan interface AI Agent.

---

## 📋 Prasyarat System

Sebelum memulai, pastikan perangkat Anda memiliki:
- Sistem Operasi Windows
- **Git** sudah terinstal di komputer.
- Internet (hanya untuk proses download awal).

---

## 🛠️ Langkah-Langkah Instalasi

### 1. Instalasi Node.js
Buka **Command Prompt (CMD)** dan jalankan perintah berikut untuk menginstal Node.js LTS:

```bash
winget install -e --id OpenJS.NodeJS.LTS
```

---

### 2. Setup Server AI (`llama.cpp`)

1. **Download llama.cpp:**
   - Kunjungi [llama.cpp Releases](https://github.com/ggml-org/llama.cpp/releases?page=1).
   - Unduh (download) file rilis yang sesuai dengan sistem operasi (OS/GPU) komputer Anda.

2. **Ekstrak File:**
   - Buat folder baru bernama `ai-lokal` di direktori penyimpanan utama (misalnya `C:\ai-lokal`).
   - Ekstrak seluruh isi file zip `llama.cpp` yang telah didownload ke dalam folder `ai-lokal`.

3. **Download Model AI (Qwen):**
   - Unduh file model dari link berikut: [Qwen3-4B-Instruct GGUF](https://huggingface.co/bartowski/Qwen_Qwen3-4B-Instruct-2507-GGUF/blob/main/Qwen_Qwen3-4B-Instruct-2507-Q4_K_M.gguf).
   - Setelah selesai mendownload, **Pindahkan (Cut/Copy)** file `Qwen_Qwen3-4B-Instruct-2507-Q4_K_M.gguf` ke dalam folder `ai-lokal`.

4. **Uji Coba Running Server AI:**
   - Buka CMD di dalam folder `ai-lokal`, lalu jalankan perintah:
     ```bash
     llama-server.exe -m Qwen_Qwen3-4B-Instruct-2507-Q4_K_M.gguf --port 8080
     ```
   - Jika server berhasil berjalan (running), **tutup CMD tersebut terlebih dahulu** untuk melanjutkan ke proses berikutnya.

---

### 3. Setup Project AI Agent Client

1. **Clone Repository:**
   - Buat folder baru di luar folder `ai-lokal`, beri nama misalnya `ai-lokal1`.
   - Buka folder `ai-lokal1` menggunakan **VS Code** (atau buka terminal di direktori tersebut).
   - Di terminal VScode, jalankan perintah clone repository:
     ```bash
     git clone https://github.com/Devanrifan/kantor-ai-agent-local
     ```

2. **Konfigurasi Environment (`.env`):**
   - Di dalam folder project `kantor-ai-agent-local`, buat file baru bernama `.env`.
   - Salin (copy) seluruh isi dari file `env.example` ke file `.env` yang baru dibuat.
   - Cari baris `ACCESS_CODE=` dan isi dengan kode `123`.

     ```env
     # Kode yang harus dimasukkan pengunjung sebelum bisa chat. WAJIB diisi kalau situs publik.
     ACCESS_CODE=123
     ```

---

## 🚀 Cara Menjalankan Aplikasi

Untuk menjalankan AI Agent, Anda perlu membuka 2 jendela terminal / CMD secara bersamaan:

### Step A: Jalankan Server LLM
Buka CMD di folder `ai-lokal` dan jalankan perintah:
```bash
llama-server.exe -m Qwen_Qwen3-4B-Instruct-2507-Q4_K_M.gguf --port 8080
```
> ⚠️ **Catatan:** Jangan tutup jendela CMD ini selama Anda menggunakan AI Agent.

### Step B: Jalankan Web Client AI Agent
Buka terminal/CMD baru di folder project `ai-lokal1` (atau di dalam repo `kantor-ai-agent-local`), lalu jalankan:

1. **Instalasi Dependensi:**
   ```bash
   npm install
   ```
   *(Tunggu hingga proses instalasi selesai dan menampilkan output seperti `found 0 vulnerabilities`)*

2. **Jalankan Web Application:**
   ```bash
   npm run dev
   ```

---

## 🌐 Akses Aplikasi

Setelah berhasil menjalankan `npm run dev`, terminal akan menampilkan URL akses lokal dan jaringan:

```text
[web]   ➜  Local:   http://localhost:5173/
[web]   ➜  Network: http://192.168.56.1:5173/  Ethernet
[web]   ➜  Network: http://192.168.1.20:5173/  Wi-Fi
```

Buka browser Anda dan akses salah satu alamat di atas (misalnya `http://localhost:5173/`). Masukkan kode akses `123` saat diminta untuk mulai menggunakan AI Agent.