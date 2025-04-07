# 📝 Git Cheatsheet (Ringkasan Perintah Git Sehari-hari)

## 🔧 Setup Awal

```bash
git config --global user.name "Nama Kamu"
git config --global user.email "email@example.com"
git init                      # Inisialisasi repo lokal
git clone <url>              # Clone repo dari remote
```

## 🔍 Cek Status & Info

```bash
git status                   # Lihat perubahan
git log                      # Lihat histori commit
```

## 🛠️ Staging & Commit

```bash
git add .                    # Tambah semua perubahan
git add <file>              # Tambah file tertentu
git commit -m "pesan"        # Commit perubahan
git commit --amend           # Edit commit terakhir
```

## 🔀 Branching & Merging

```bash
git branch                   # Lihat daftar branch
git checkout -b <nama>       # Buat & pindah branch baru
git checkout <nama>          # Pindah branch
git merge <branch>           # Gabungkan branch
```

## 🔁 Rebase vs Merge

```bash
# Merge (membuat commit baru saat penggabungan)
git checkout main
git merge feature-branch

# Rebase (menyusun ulang commit agar linear)
git checkout feature-branch
git rebase main
```

## 🔄 Sinkronisasi dengan Remote

```bash
git pull origin <branch>     # Tarik perubahan
git pull --rebase            # Tarik dengan rebase
git push origin <branch>     # Kirim perubahan
```

## 🧹 Reset, Revert, Stash

```bash
git reset --soft HEAD~1      # Undo commit, simpan perubahan
git reset --hard HEAD~1      # Hapus commit dan perubahan

git checkout -- <file>       # Buat file kembali seperti commit terakhir
git revert <hash>            # Bikin commit baru untuk membatalkan commit tertentu

git stash                    # Simpan perubahan sementara
git stash list               # Lihat daftar stash
git stash pop                # Ambil stash terakhir
```

## 🌐 Remote & URL

```bash
git remote -v                # Lihat remote
git remote add origin <url>  # Tambah remote
```

## 🔁 Alur Kerja Git (Simplified Git Flow)

1. Buat branch baru untuk setiap fitur atau bugfix
2. Kerjakan di branch tersebut
3. Commit perubahan secara bertahap
4. Push ke remote
5. Buka pull request ke `main` / `develop`
6. Review & merge

```bash
git checkout -b fitur/login
# kerja, commit, push
# lalu buka pull request di GitHub
```

## 📌 Tips Cepat

- Selalu `pull` sebelum mulai kerja
- Gunakan branch untuk fitur baru
- Commit kecil dan jelas
- Gunakan `.gitignore` untuk file tidak penting
- Review pakai `git diff` sebelum commit
- Tambahkan deskripsi di setiap pull request

---

💬 **Butuh referensi cepat?** Ketik `git help <perintah>` atau lihat dokumentasi di
[git-scm.com](https://git-scm.com)
