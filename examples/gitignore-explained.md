# 📁 Penjelasan .gitignore

`.gitignore` adalah file konfigurasi yang digunakan Git untuk mengabaikan file atau
folder tertentu supaya tidak ikut ter-track, tidak di-commit, dan tidak dikirim ke
repo remote.

Ini penting agar:

- Repository tetap ringan dan bersih
- File sensitif tidak ikut terunggah (misalnya token API, credential, dll)
- File sementara dan hasil build tidak mengganggu kolaborasi

## 📌 Contoh File/Folder yang Umum Diabaikan

- `.env` — file yang berisi konfigurasi rahasia
- `node_modules/` — dependency dari proyek Node.js
- `*.log`, `*.tmp`, `*.cache` — file log, cache, dan sementara
- `dist/`, `build/`, `coverage/` — hasil build atau output dari tools
- `.vscode/`, `.idea/` — konfigurasi editor lokal
- `__pycache__/`, `*.pyc` — cache Python

> Tips: Gunakan [gitignore.io](https://www.toptal.com/developers/gitignore) untuk
> membuat `.gitignore` sesuai jenis proyek secara otomatis.
